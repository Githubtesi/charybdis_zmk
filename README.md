# Charybdis 4x6 Wireless (Trackball) – ZMK Config

このリポジトリは、**Charybdis 4×6（トラックボール付き）Wireless 版**の
**ZMK Firmware 用キー設定（keymap）**を管理するためのものです。

* 左右分離
* 4×6 レイアウト
* トラックボール（マウス操作）対応
* Bluetooth（ZMK / nRF52）
* 日本語入力（IME）・プログラミング用途最適化

---

## 🧩 ハードウェア構成

* **Keyboard**: Charybdis 4×6
* **Firmware**: ZMK
* **MCU**: nRF52 系
* **接続方式**: Bluetooth（Wireless）
* **ポインティングデバイス**: トラックボール内蔵

---

## 🛠 Keymap Editor について

Keymap Editor（Web UI）は以下の用途で使用します。

* 各キーの **position 番号確認**
* レイヤー構成の視覚的確認
* 単キー割り当ての調整

**Combo / 高度な設定は GitHub 上で編集します。**

---

## 🔨 ビルド方法（GitHub Actions）

1. このリポジトリを Fork
2. `config/` 以下を編集
3. GitHub に push
4. **Actions → Build ZMK firmware**
5. 生成された `.uf2` / `.bin` を書き込み

---

## 📄 License

MIT License
