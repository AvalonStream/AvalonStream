# Avalon

### Windows 10/11 x64 PC 한 대. 서로 독립된 여러 데스크톱.

Avalon은 하나의 Windows 10/11 x64 호스트를 여러 개의 독립적으로 접속 가능한 데스크톱 인스턴스로 확장합니다. 각 인스턴스는 자체 Windows 세션, 가상 디스플레이, 입력, 오디오, 앱, 게임 및 Moonlight 연결을 가질 수 있습니다.

**하나의 호스트. 여러 인스턴스.**

[English](README.md)

[개발 로그 및 피드백](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / 버그 및 기능 제안](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon이란?

Avalon은 Windows 10/11 x64용 멀티 세션 데스크톱 스트리밍 플랫폼입니다. 한 대의 PC를 하나의 대화형 데스크톱에만 묶어 두는 대신, 사용자마다 완전한 가상 머신을 만들지 않고 여러 Windows 인스턴스를 같은 호스트에서 동시에 실행합니다.

---

## 핵심 기능

- 한 호스트에서 여러 개의 독립 Windows 인스턴스 실행
- 인스턴스별 독립 스트리밍 컨텍스트
- 인스턴스별 가상 디스플레이, 해상도 및 주사율
- 키보드, 마우스 및 세션 오디오 경로 분리
- 외부 RDP 클라이언트를 계속 연결하지 않아도 Avalon이 세션 수명 주기 유지
- Web에서 생성, 페어링, 상태 확인 및 진단
- 휴대폰, 태블릿, TV, PC에서는 익숙한 Moonlight 클라이언트 사용

---

## 동작 방식

인스턴스를 만들고 디스플레이 설정을 선택한 뒤 클라이언트를 페어링합니다. Avalon이 Windows 세션, 가상 디스플레이, 스트리밍 컨텍스트와 수명 주기를 준비하면 Moonlight로 연결합니다.

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Moonlight를 위한 설계

Avalon은 호스트 측을 바꾸며 기존 클라이언트를 대체하지 않습니다. Moonlight는 Windows, Linux, macOS, Android, iOS/iPadOS, Android TV 등에서 계속 사용할 수 있습니다.

---

## 대표 사용 사례

- 가정용 게임: 서로 다른 사용자가 각자 인스턴스를 동시에 사용
- 다중 계정 및 다중 인스턴스 작업
- 고성능 PC 한 대를 여러 원격 워크스테이션으로 활용
- 테스트, 자동화 및 호환성 환경
- Homelab 및 셀프 호스팅 원격 컴퓨팅

---

## 격리 모델

Avalon은 완전한 가상 머신이 아니라 Windows 세션 수준의 격리를 제공합니다. 데스크톱, 앱, 디스플레이, 입력 및 오디오는 인스턴스별로 분리되지만 호스트 Windows, 커널, CPU, GPU 및 실제 하드웨어는 공유합니다. VM 수준의 보안 경계로 간주해서는 안 됩니다.

---

## 플랫폼 및 성능

Avalon은 64비트 Windows 10과 Windows 11을 대상으로 합니다. 실제 해상도, 주사율, 코덱, HDR 및 동시 인스턴스 수는 GPU, 드라이버, 인코더, 네트워크 및 클라이언트 하드웨어에 따라 달라집니다.

---

## 프로젝트 상태

Avalon은 현재 Alpha 단계입니다. UI, 호환성 동작 및 저수준 구성 요소가 계속 변경되고 있으므로 호환성을 깨는 변경이나 특정 하드웨어의 예외 상황이 발생할 수 있습니다.

---

## 개발 정보와 피드백

이 README는 안정적인 제품 소개용입니다. 실시간 개발 동향과 메시지 안내는 별도의 개발 로그에서 관리합니다.

- [개발 로그 및 피드백](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / 버그 및 기능 제안](https://github.com/AvalonStream/AvalonStream/issues)

**하나의 호스트. 여러 인스턴스.**
