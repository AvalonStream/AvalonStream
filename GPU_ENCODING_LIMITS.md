# GPU Hardware Encoding Limits & Multi-Instance Streaming

> **Avalon hardware compatibility reference**  
> Covers NVIDIA NVENC, Intel Quick Sync Video (QSV), and AMD Advanced Media Framework (AMF).  
> Last reviewed: October 2026.

Avalon is designed for managing multiple independent Windows desktop instances. However, the number of Windows instances you can create or start is **not necessarily the number of simultaneous video streams your GPU can encode**.

When using Avalon with a streaming client such as Moonlight, your GPU's hardware video encoder may become a limiting factor. Different GPU vendors apply different encoding policies and hardware constraints.

This document explains those differences and helps you understand what to check if additional instances or streams fail to start.

## 1. Understand the Different Limits

These terms are **not interchangeable**:

| Term | Meaning |
| --- | --- |
| **Windows session** | An independent Windows desktop or user session. |
| **Avalon instance** | A desktop instance managed by Avalon. |
| **Streaming connection** | A client actively receiving a video stream from a host. |
| **Hardware encoding session** | An active video encoder context created through NVENC, QSV, AMF, or another backend. |
| **Hardware encoder engine** | A physical GPU component responsible for accelerating video encoding. |

An idle Windows console session does **not** automatically consume a hardware encoding session. Likewise, an Avalon instance does not necessarily consume an encoding session simply because it exists. The actual behavior depends on when its streaming backend initializes and releases the encoder.

**Important:** A GPU with multiple physical encoding engines does not necessarily allow an unlimited number of encoding sessions.

## 2. GPU Vendor Comparison

| GPU / Vendor | Encoding Technology | Concurrent Encoding Limit |
| --- | --- | --- |
| **NVIDIA GeForce** (supported NVENC models) | NVENC | **12 concurrent sessions in total across non-qualified NVIDIA GPUs in one system**, according to NVENC SDK 13.1. |
| **NVIDIA professional / data-center GPUs** | NVENC | **Model-dependent.** The official matrix may show `Unrestricted`, a numerical limit such as `8`, or no encoding support. |
| **Intel integrated graphics / Intel Arc** | Quick Sync Video / Intel VPL | No comparable universal, vendor-published 12-session licensing cap identified. Actual concurrency is hardware-, driver-, and workload-dependent. |
| **AMD Radeon / Radeon PRO** | AMF / VCE / VCN | No comparable universal 12-session licensing cap identified. Supported concurrency is hardware-, driver-, and codec-dependent; AMF exposes capability queries. |

**No fixed licensing cap does not mean unlimited real-time streams.** Encoding throughput, memory, codec support, operating-system resources, GPU utilization, and other active applications can limit performance or prevent new encoders from starting.

## 3. NVIDIA — NVENC

### Consumer GeForce GPUs

NVIDIA's **Video Codec SDK 13.1** distinguishes *qualified* and *non-qualified* GPUs:

- On **non-qualified GPUs**, NVIDIA documents a maximum of **12 concurrent NVENC encoding sessions per system**.
- The 12-session limit is **shared across all non-qualified NVIDIA GPUs** in the same system; it is not 12 sessions per card.
- On **qualified GPUs**, the documented limit is based on hardware and available system resources rather than that fixed non-qualified session ceiling.

Examples from NVIDIA's current support matrix:

| GPU | Maximum Concurrent NVENC Sessions |
| --- | --- |
| GeForce RTX 3090 | 12 |
| GeForce RTX 4090 | 12 |
| GeForce RTX 5090 | 12 |
| NVIDIA RTX A400 | 8 (as listed in the GPU support matrix) |
| NVIDIA RTX A2000 | Unrestricted |
| NVIDIA RTX PRO 6000 Blackwell Workstation Edition | Unrestricted |

For example, installing **two GeForce RTX 4090 cards does not raise the non-qualified NVENC limit to 24 sessions**. Their combined documented allowance remains 12.

An `Unrestricted` entry means **there is no fixed session count shown in that matrix**; it does **not** guarantee unlimited 1080p60 or 4K streams. Practical performance is still limited by the GPU's encoder throughput and available resources.

Also note that **some NVIDIA cards have no NVENC encoder at all**. Check the precise GPU model rather than assuming every NVIDIA GPU supports hardware encoding.

**Check your GPU:** [NVIDIA Video Encode and Decode Support Matrix](https://developer.nvidia.com/video-encode-decode-support-matrix) — look for **Max # of concurrent sessions**.

### Monitor Active NVIDIA Encoder Sessions

On supported drivers, run the following in PowerShell or Command Prompt:

```powershell
nvidia-smi encodersessions
```

This can help identify the NVENC sessions currently in use. If the command is unavailable on your installed driver, refer to your `nvidia-smi` help output or NVIDIA's official documentation.

Other applications—including game streamers, screen recorders, and video encoders—may consume NVENC sessions. A GPU's limit is **not reserved exclusively for Avalon**.

## 4. Intel — Quick Sync Video (QSV)

Intel graphics hardware supports video encoding through **Quick Sync Video**, commonly accessed through Intel Media SDK (legacy) or **Intel Video Processing Library (VPL)**.

Intel VPL explicitly supports **multiple independent sessions** and simultaneous encoding operations. In the reviewed public VPL documentation, there is **no NVIDIA-style universal 12-session licensing rule**.

However, the maximum number of streams that will work on a particular Intel GPU depends on factors such as:

- GPU generation and available media processing resources.
- Codec support (for example, H.264, HEVC, or AV1, where supported).
- Resolution, frame rate, encoding quality, and bit depth.
- Driver and VPL runtime versions.
- Available memory and the load from other graphics applications.

**Do not interpret “no fixed licensing cap” as “unlimited concurrent encoding.”** Multiple encoder sessions may initialize successfully but still be unable to sustain the requested frame rates.

See [Intel VPL — Sessions and Multiple Sessions](https://github.com/intel/libvpl/blob/main/doc/spec/source/programming_guide/VPL_prg_session.rst).

## 5. AMD — Advanced Media Framework (AMF)

AMD uses **AMF** to expose video encoding capabilities backed by hardware video engines such as VCE and VCN.

The reviewed AMD documentation does not specify a universal, NVIDIA-style 12-session licensing limit for all Radeon GPUs. Instead, AMF offers **device- and codec-specific capability queries**.

For H.264, relevant AMF properties include:

| AMF Capability | Description |
| --- | --- |
| `AMF_VIDEO_ENCODER_CAP_NUM_OF_STREAMS` | Maximum number of encode streams reported as supported. |
| `AMF_VIDEO_ENCODER_CAP_NUM_OF_HW_INSTANCES` | Number of hardware encoder instances reported. |
| `AMF_VIDEO_ENCODER_CAP_MAX_THROUGHPUT` | Reported maximum encoding throughput. |
| `AMF_VIDEO_ENCODER_CAP_REQUESTED_THROUGHPUT` | Currently requested encoding throughput. |

For HEVC, corresponding properties include `AMF_VIDEO_ENCODER_HEVC_CAP_NUM_OF_STREAMS` and `AMF_VIDEO_ENCODER_HEVC_CAP_NUM_OF_HW_INSTANCES`. Available capability fields may differ for other codecs, including AV1.

AMD provides an official **CapabilityManager** sample demonstrating how to query the information exposed by AMF:

[AMD AMF — CapabilityManager.cpp](https://github.com/GPUOpen-LibrariesAndSDKs/AMF/blob/master/amf/public/samples/CPPSamples/CapabilityManager/CapabilityManager.cpp)

**Important:** The hardware engine count and maximum stream count are different concepts. Additionally, older AMF settings such as `AMF_VIDEO_ENCODER_MAX_INSTANCES` are marked deprecated; their historical defaults should **not** be treated as a universal Radeon encoding limit.

The fact that an AMD GPU supports AMF also does not imply that every codec or hardware encoding mode is available on that GPU.

## 6. Why Can the Next Avalon Instance or Stream Fail?

Consider this example:

```text
Windows console session                  1
Running Avalon desktop instances        12
------------------------------------------
Total Windows sessions                  13

Active NVENC encoding sessions          12  (example)
Attempt to initialize another NVENC     FAIL (possible 12-session ceiling)
```

If 12 Avalon streams each hold one NVENC session on a non-qualified NVIDIA GPU, a request for a 13th encoding session can fail because the driver's documented concurrent-session limit has already been reached.

**This is an example, not proof that every Avalon instance allocates an NVENC session on startup.** The failure could also occur elsewhere—during Windows session creation, display initialization, memory allocation, driver initialization, or streaming backend startup.

If your configuration encounters a similar problem, try the following:

1. Identify your GPU model, driver version, and selected encoding backend.
2. Stop unrelated screen recorders or streaming applications that may be using the GPU encoder.
3. On NVIDIA systems, inspect active encoder sessions using `nvidia-smi encodersessions`.
4. Test whether the issue occurs when creating an Avalon instance, starting it, or only when a Moonlight client connects.
5. Stop one active stream, verify that its encoder resources have been released, and retry the failed operation.
6. Record the exact error message and relevant logs before reporting a problem.

If stopping one active stream immediately allows another stream to start, an encoder resource or concurrency limit becomes a stronger possibility—but still requires confirmation from logs or driver diagnostics.

## 7. What Determines Real-World Multi-Stream Performance?

Regardless of GPU vendor, maximum practical streaming capacity can be affected by:

- **Resolution and frame rate:** Multiple 4K60 streams generally demand far more resources than 1080p30 streams.
- **Codec:** H.264, HEVC, and AV1 have different hardware support and performance characteristics.
- **Encoding preset and quality settings:** Higher-quality modes can require more encoder capacity.
- **Available VRAM and system memory:** Every session and streaming pipeline has resource overhead.
- **GPU and CPU workload:** Games and other programs still need rendering and processing resources.
- **Other active encoders:** OBS, recording applications, and other streaming services may use the same hardware encoder.
- **Drivers and operating-system compatibility:** Driver behavior, resource allocation, and API support can vary.

A high configured-instance count should therefore **never be interpreted as a guaranteed number of simultaneous hardware-encoded streams**.

## 8. Official References

**NVIDIA**

- [NVENC Application Note — Licensing Policy (Video Codec SDK 13.1)](https://docs.nvidia.com/video-technologies/video-codec-sdk/13.1/nvenc-application-note/index.html)
- [Video Encode and Decode GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-support-matrix)
- [NVIDIA System Management Interface (nvidia-smi)](https://docs.nvidia.com/deploy/nvidia-smi/index.html)

**Intel**

- [Intel Video Processing Library (VPL)](https://github.com/intel/libvpl)
- [VPL — Multiple Sessions](https://github.com/intel/libvpl/blob/main/doc/spec/source/programming_guide/VPL_prg_session.rst)

**AMD**

- [AMD Advanced Media Framework (AMF)](https://github.com/GPUOpen-LibrariesAndSDKs/AMF)
- [AMF — H.264 Video Encode API](https://github.com/GPUOpen-LibrariesAndSDKs/AMF/blob/master/amf/doc/AMF_Video_Encode_API.md)
- [AMF — HEVC Video Encode API](https://github.com/GPUOpen-LibrariesAndSDKs/AMF/blob/master/amf/doc/AMF_Video_Encode_HEVC_API.md)
- [AMF — CapabilityManager Sample](https://github.com/GPUOpen-LibrariesAndSDKs/AMF/blob/master/amf/public/samples/CPPSamples/CapabilityManager/CapabilityManager.cpp)

---

> **Disclaimer:** This document summarizes publicly available vendor information as of the review date. GPU and driver policies may change. Actual Avalon support for a GPU or encoding backend depends on the installed Avalon release and configuration. For authoritative limits and compatibility details, always consult the latest vendor documentation.

**Avalon:** [Official website](https://avalons.cc) · [GitHub repository](https://github.com/AvalonStream/AvalonStream) · [Support / Issues](https://github.com/AvalonStream/AvalonStream/issues)
