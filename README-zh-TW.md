# Avalon

### 一台 Windows 10/11 x64，多個彼此獨立的桌面。

Avalon 能把一台 Windows 10/11 x64 主機變成多個可獨立存取的桌面實例。每個實例都能擁有自己的 Windows 工作階段、虛擬顯示、輸入、音訊、應用程式、遊戲與 Moonlight 連線。

**一台主機，多個實例。**

[English](README.md)

[開發日誌與留言說明](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / 錯誤與功能建議](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon 是什麼？

Avalon 是面向 Windows 10/11 x64 的多工作階段桌面串流平台。它讓多個獨立 Windows 實例能同時運行在同一台主機上，而不需要為每位使用者建立完整虛擬機。

---

## 核心能力

- 一台主機同時運行多個獨立 Windows 實例
- 每個實例都有獨立串流上下文
- 每實例獨立虛擬顯示、解析度與更新率
- 獨立鍵盤、滑鼠與工作階段音訊路徑
- Avalon 維持工作階段生命週期，不需外部 RDP 客戶端持續連線
- 透過 Web 建立實例、配對、查看狀態與診斷
- 手機、平板、電視與 PC 仍使用熟悉的 Moonlight 客戶端

---

## 它如何運作？

建立實例、選擇顯示設定並完成客戶端配對。Avalon 會準備 Windows 工作階段、虛擬顯示、串流上下文與生命週期，之後直接以 Moonlight 連線。

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

## 為 Moonlight 而設計

Avalon 改變的是主機端，而不是取代既有客戶端。Moonlight 仍可在 Windows、Linux、macOS、Android、iOS/iPadOS、Android TV 與其他支援裝置上使用。

---

## 典型使用情境

- 家庭遊戲：不同使用者同時進入不同實例
- 多帳號、多開與多實例工作負載
- 將一台高效能 PC 當作多個遠端工作站
- 測試、自動化與相容性環境
- Homelab 與自架遠端運算

---

## 隔離模型

Avalon 提供 Windows 工作階段層級隔離，而不是完整虛擬機隔離。實例有各自的桌面、應用程式、顯示、輸入與音訊路徑，但仍共享主機 Windows、核心、CPU、GPU 與實體硬體，因此不應視為 VM 等級的安全邊界。

---

## 平台與效能

Avalon 面向 64 位元 Windows 10 與 Windows 11。實際解析度、更新率、編碼格式、HDR 表現與同時實例數量取決於 GPU、驅動程式、編碼能力、網路與客戶端硬體。

---

## 專案狀態

Avalon 目前處於 Alpha 階段。介面、相容性與底層元件仍持續演進，可能出現破壞性變更與特定硬體的邊緣問題。

---

## 開發動態與回饋

這份 README 用於穩定的產品介紹。即時開發動態與留言說明會另外維護在開發日誌中。

- [開發日誌與留言說明](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / 錯誤與功能建議](https://github.com/AvalonStream/AvalonStream/issues)

**一台主機，多個實例。**
