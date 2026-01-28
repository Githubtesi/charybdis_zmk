# Charybdis 4x6 Wireless (Trackball) – ZMK Config

このリポジトリは、**Charybdis 4×6（トラックボール付き）Wireless 版**の **ZMK Firmware 用キー設定（keymap）**を管理するためのものです。

* 左右分離 / 4×6 レイアウト
* トラックボール（マウス操作）対応
* Bluetooth（ZMK / nRF52）
* 日本語Windows環境（JIS認識）へのローカライズ対応

---

## 🧩 ハードウェア構成

* **Keyboard**: Charybdis 4×6
* **Firmware**: ZMK
* **MCU**: nRF52 系 (nice!nano 等)
* **接続方式**: Bluetooth（Wireless）
* **ポインティングデバイス**: トラックボール内蔵

---

## 🛠 キーマップの編集方法

本リポジトリのキーマップ編集は、Web UI を備えたエディタを推奨します。

1. **[Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)** にアクセスします。
2. 本リポジトリを連携（GitHub Authorize）させます。
3. ブラウザ上でキー配置を編集し、「Save」ボタンを押すと自動的にGitHubへコミットされます。

*※Comboや高度な挙動の微調整を直接コードで行う場合は、GitHub上の `config/charybdis.keymap` を編集してください。*

---

## 🇯🇵 日本語Windows（JIS認識）への対応

US配列のCharybdisを、JIS認識設定のWindowsで「刻印通り」に使うためには、以下の外部プロジェクトを活用したローカライズを推奨します。

### 方法A：ZMK内部でのローカライズ
**外部ソフトを使用せず、キーボード単体でUS刻印通りの入力を実現する方法です。**

1. Keymap Editorで通常のUS配列としてキーマップを保存します。
2. 外部プロジェクト [charybdis-zmk-jp-localizer](https://github.com/あなたのユーザー名/charybdis-zmk-jp-localizer) の `localize_keymap.py` を使用し、本リポジトリの `charybdis.keymap` をJIS変換します。
3. 変換後の内容をGitHubへ反映（Push）することで、どのPCに繋いでもUS刻印通りの入力が可能になります。

### 方法B：AutoHotkeyによるローカライズ
**PC側に常駐ソフトを入れ、リアルタイムに入力信号を変換する方法です。**

1. キーボード側は標準のUS配列のままビルドします。
2. 外部プロジェクト [charybdis-us-to-jis-remap](https://github.com/あなたのユーザー名/charybdis-us-to-jis-remap) のAutoHotkeyスクリプトをWindows上で実行します。

---

## 🔨 ビルド方法（GitHub Actions）

1. **[Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)** を使用してキーマップを編集・保存します。
2. GitHub に変更が反映されると、自動的に GitHub Actions が走りファームウェアがビルドされます。
3. **Actions タブ** から最新のビルド結果（Artifacts）をダウンロードします。
4. 解凍して得られる `.uf2` ファイルを、各MCU（nice!nano等）に書き込んでください。

---

## 📄 License

MIT License
