# Charybdis 4x6 Wireless (Trackball) – ZMK Config

このリポジトリは、**Charybdis 4×6（トラックボール付き）Wireless 版**の **ZMK Firmware 用キー設定（keymap）**を管理・ビルドするためのものです。

* 左右分離 / 4×6 レイアウト
* トラックボール（マウス操作）対応
* Bluetooth（ZMK / nice!nano 等の nRF52 MCU）
* 日本語Windows環境（JIS認識）へのローカライズ対応

---

## 🧩 ハードウェア構成

* **Keyboard**: Charybdis 4×6
* **Firmware**: ZMK
* **MCU**: nRF52 系 (nice!nano 等)
* **接続方式**: Bluetooth（Wireless）
* **ポインティングデバイス**: トラックボール内蔵

---

## 🚀 はじめかた（ビルド手順）

### 1. リポジトリの準備
1. このリポジトリを自身のGitHubアカウントに **Fork** してください。
2. Fork したリポジトリの **Actions** タブを開き、「I understand my workflows, go ahead and enable them」をクリックして GitHub Actions を有効にします。

### 2. キーマップの編集
本リポジトリの編集は **Keymap Editor** を推奨します。

1. **[Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)** にアクセスします。
2. Fork した自身のリポジトリを選択・連携させます。
3. ブラウザ上の UI でキー配置を自由に編集し、「Save」を押します。
4. これにより、GitHub 上の `config/charybdis.keymap` が自動的に更新されます。

---

## 🇯🇵 日本語Windows（JIS認識）へのローカライズ

US配列のCharybdisを、JIS認識設定のWindowsで「刻印通り」に使うためには、以下の外部プロジェクトを活用してください。

### 方法A：ZMK内部でのローカライズ
**外部ソフトを使用せず、キーボード単体でUS刻印通りの入力を実現します。**

1. Keymap Editorで通常のUS配列としてキーマップを保存します。
2. 別リポジトリ [charybdis-zmk-jp-localizer](https://github.com/Githubtesi/charybdis-zmk-jp-localizer) の `localize_keymap.py` を実行し、本リポジトリの `charybdis.keymap` を変換します。
3. 変換後の内容をGitHubへ反映（Push）してください。

### 方法B：AutoHotkeyによるローカライズ
**PC側に常駐ソフトを入れ、リアルタイムに入力信号を変換します。**

1. キーボード側は標準のUS配列のままビルドします。
2. 別リポジトリ [charybdis-us-to-jis-remap](https://github.com/Githubtesi/charybdis-us-to-jis-remap) のAutoHotkeyスクリプトをWindows上で実行します。

---

## 📦 ファームウェアの書き込み

1. GitHub 上のファイルが更新されると、自動的に **GitHub Actions** でビルドが開始されます。
2. **Actions** タブから最新のワークフロー実行（Build）を選択します。
3. 画面下部の **Artifacts** から、ビルドされたファームウェア（`.zip`）をダウンロードします。
4. 解凍して得られる `.uf2` ファイルを以下の手順で書き込みます。
   - キーボードをPCに接続し、MCU（nice!nano等）のリセットボタンを素早く2回押してブートローダーモード（外付けドライブとして認識）にします。
   - 対応する `.uf2` ファイルをドライブにドラッグ＆ドロップします。

---

## 📄 License

MIT License
