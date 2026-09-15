# Avalon

### 1 台の Windows 10/11 x64 PC。複数の独立したデスクトップ。

Avalon は 1 台の Windows 10/11 x64 ホストを、個別にアクセスできる複数のデスクトップインスタンスへ拡張します。各インスタンスは独自の Windows セッション、仮想ディスプレイ、入力、音声、アプリ、ゲーム、Moonlight 接続を持てます。

**1 台のホスト。複数のインスタンス。**

[English](README.md)

[開発ログとフィードバック](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / バグ・機能要望](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon とは？

Avalon は Windows 10/11 x64 向けのマルチセッション・デスクトップストリーミング基盤です。PC 全体を 1 つの対話型デスクトップだけに使うのではなく、完全な仮想マシンをユーザーごとに用意せず、複数の独立した Windows インスタンスを同じホスト上で並行して動かします。

---

## 主な機能

- 1 台のホストで複数の独立 Windows インスタンスを実行
- インスタンスごとに独立したストリーミングコンテキスト
- インスタンスごとの仮想ディスプレイ、解像度、リフレッシュレート
- キーボード、マウス、セッション音声の独立経路
- 外部 RDP クライアントを常時接続せず Avalon がセッションを維持
- Web から作成、ペアリング、状態確認、診断
- スマートフォン、タブレット、TV、PC では従来どおり Moonlight を利用

---

## 仕組み

インスタンスを作成し、表示設定を選び、クライアントをペアリングします。Avalon が Windows セッション、仮想ディスプレイ、ストリーミング環境、ライフサイクルを準備し、その後 Moonlight から接続します。

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

## Moonlight のための設計

Avalon が変えるのはホスト側です。使い慣れたクライアントを置き換える必要はありません。Moonlight は Windows、Linux、macOS、Android、iOS/iPadOS、Android TV などで引き続き利用できます。

---

## 代表的な用途

- 家庭内ゲーム：複数人が別々のインスタンスを同時利用
- 複数アカウント・複数インスタンス運用
- 1 台の高性能 PC を複数のリモートワークステーションとして利用
- テスト、自動化、互換性検証環境
- Homelab とセルフホスト型リモートコンピューティング

---

## 分離モデル

Avalon が提供するのは Windows セッションレベルの分離であり、完全な仮想マシン分離ではありません。デスクトップ、アプリ、表示、入力、音声はインスタンスごとに分離されますが、Windows ホスト、カーネル、CPU、GPU、物理ハードウェアは共有されます。VM 相当のセキュリティ境界として扱うべきではありません。

---

## 対応プラットフォームと性能

Avalon は 64 ビット版 Windows 10 / Windows 11 を対象とします。解像度、リフレッシュレート、コーデック、HDR、同時インスタンス数は GPU、ドライバー、エンコーダー、ネットワーク、クライアント性能に依存します。

---

## プロジェクト状況

Avalon は現在 Alpha 段階です。UI、互換性、低レイヤーの構成は継続的に変更されており、破壊的変更や特定ハードウェアでの問題が発生する可能性があります。

---

## 開発情報とフィードバック

この README は安定した製品紹介です。リアルタイムの開発状況とメッセージ案内は開発ログに分けて管理します。

- [開発ログとフィードバック](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / バグ・機能要望](https://github.com/AvalonStream/AvalonStream/issues)

**1 台のホスト。複数のインスタンス。**
