---
title: Espanso
description: Rust製・オープンソースのクロスプラットフォーム・テキストエキスパンダー
---

# Espanso (テキストエキスパンダー / 入力支援)

[Espanso](https://espanso.org/) は、Rust で記述されたオープンソースかつプライバシー重視のクロスプラットフォーム・テキストエキスパンダー（スニペット・定型文展開ツール）です。  
あらかじめ登録したキーワード（トリガー）を入力すると、瞬時に対応する文章・コード片・動的データに置き換えてくれます。

---

## 1. 概要 & 選定理由

- **Pure Rust による超軽量・高速動作**: 常時バックグラウンドでキー入力を監視していても、CPU・メモリリソースの消費が極めて小さく、入力の遅延が一切ありません。
- **YAML 形式によるコードベース管理**: 設定やスニペットはすべてプレーンな YAML ファイルで記述されるため、Git や dotfiles でバージョン管理・環境同期が容易です。
- **動的拡張（シェル実行・スクリプト連携）**: 静的な文字列だけでなく、現在の日時、クリップボードの内容、シェルコマンド（PowerShell, Bash, Python 等）の実行結果をスニペット内に動的に埋め込めます。
- **クロスプラットフォーム統一**: Windows, macOS, Linux で同じ設定ファイルがそのまま利用できるため、OSを跨いだ開発環境でも入力体験が途切れません。
- **フォーム機能（GUI入力補完）**: 変数を含む定型文（メールテンプレートや報告フォーマット等）を呼び出す際、ポップアップフォームを表示して必要な項目を穴埋め入力できます。

---

## 2. 代替対象 & 比較

| 項目 | Espanso | TextExpander / PhraseExpress | IME単語登録 |
| :--- | :--- | :--- | :--- |
| **ライセンス** | オープンソース (GPL-3.0) | 商用プロプライエタリ (サブスク) | OS標準 |
| **言語・基盤** | **Rust** (ネイティブ) | C++ / Electron | OS標準 |
| **設定管理** | **YAML (Git/dotfiles同期可)** | クラウド依存 / 専用形式 | 各IMEの設定画面 |
| **動的実行** | **シェルコマンド・スクリプト連携** | スクリプト連携（有料プラン） | 不可（固定文字のみ） |
| **フォーム入力** | **GUIフォーム標準対応** | 対応（高額プラン） | 不可 |
| **プラットフォーム** | Windows, macOS, Linux | Windows, macOS | OS/IME依存 |

---

## 3. 導入手順 & インストール

### Windows での入手
推奨は `winget` によるインストールです。

```powershell
winget install Espanso.Espanso
```

または [Espanso 公式サイト](https://espanso.org/install/) からインストーラーをダウンロードして実行します。

### macOS での入手
```bash
brew tap espanso/espanso
brew install espanso
```

### サービスの開始
```bash
espanso start
```

---

## 4. 主な機能 & 活用ポイント

### 基本的なスニペット（静的展開）
`base.yml` などにトリガーと置換テキストを記述します。

```yaml
matches:
  # メールアドレス
  - trigger: ":email"
    replace: "user@example.com"

  # よく使う定型挨拶
  - trigger: ":greet"
    replace: "いつも大変お世話になっております。よろしくお願いいたします。"
```

### 動的スニペット（日時・シェルコマンド）
現在日時やコマンド出力を自動挿入します。

```yaml
matches:
  # 今日の日付 (YYYY-MM-DD)
  - trigger: ":today"
    replace: "{{mydate}}"
    vars:
      - name: mydate
        type: date
        params:
          format: "%Y-%m-%d"

  # ローカルIPアドレスの取得 (PowerShell例)
  - trigger: ":myip"
    replace: "{{output}}"
    vars:
      - name: output
        type: shell
        params:
          cmd: "(Get-NetIPAddress -AddressFamily IPv4 | Where-Object InterfaceAlias -notlike '*Loopback*').IPAddress[0]"
          shell: powershell
```

### フォーム入力機能（テンプレート作成）
展開時にフォームウィンドウが開き、プレースホルダーを入力して展開できます。

```yaml
matches:
  - trigger: ":report"
    form: |
      [[date]] 作業報告:
      - 実装内容: [[task]]
      - 所感: [[notes]]
```

---

## 5. 関連リンク
- 公式サイト: [https://espanso.org/](https://espanso.org/)
- 公式ドキュメント: [https://espanso.org/docs/](https://espanso.org/docs/)
- GitHub リポジトリ: [espanso/espanso](https://github.com/espanso/espanso)
- パッケージハブ (共有スニペット): [https://hub.espanso.org/](https://hub.espanso.org/)
