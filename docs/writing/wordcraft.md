---
title: WORDCRAFT
description: Pure Rust製・高速オープンソースワードプロセッサ（MS Word代替）
---

# WORDCRAFT (高速ワードプロセッサ)

[WORDCRAFT](https://getartcraft.com/apps/wordcraft) は、Pure Rust でスクラッチから再構築された高速かつオープンソースのネイティブ・ワードプロセッサです。  
Microsoft Word と互換性のある `.docx` 形式の読み書きに対応し、リボンUI、スタイルギャラリー、表組み、変更履歴（Track Changes）、参考文献管理、差し込み印刷などを備えています。

---

## 1. 概要 & 選定理由

- **Pure Rust による圧倒的な起動・動作速度**: 電子ドキュメントやリッチテキスト作成において、巨大で重厚なオフィススイートと比べ、瞬時に起動しメモリ消費も極めて軽量。
- **ネイティブ & オフライン完結**: クラウド同期や常時ログインを強制されず、完全にローカルオフライン環境でプライバシーを保ちながら動作。
- **.docx 完全サポート**: 標準的な Microsoft Word 文書（`.docx`）を開いて編集し、そのまま保存できるため、他者との文書共有にも支障がありません。
- **使い慣れたリボンインターフェース**: スタイル適用、文字装飾、ページレイアウト、校閲機能など、Word に近い直感的な操作感を提供。

---

## 2. 代替対象 & 比較

| 項目 | WORDCRAFT | Microsoft Word | LibreOffice Writer |
| :--- | :--- | :--- | :--- |
| **ライセンス** | オープンソース (無料) | プロプライエタリ (サブスク/有料) | オープンソース (MPL) |
| **言語・基盤** | **Pure Rust** (ネイティブ) | C++ / クラウド依存 | C++ / Java依存あり |
| **起動速度** | **爆速（即座）** | 普通〜やや重い | やや重い |
| **ファイル形式** | `.docx` | `.docx` | `.odt`, `.docx` |
| **オフライン・独立性** | **完全オフライン動作** | クラウド（OneDrive）誘導が強い | 完全オフライン動作 |
| **プラットフォーム** | Windows, macOS, Linux, Web | Windows, macOS, Web | Windows, macOS, Linux |

---

## 3. 導入手順 & インストール

### Windows / macOS / Linux
1. [GitHub Releases](https://github.com/storytold/wordcraft/releases) または [ArtCraft 公式サイト](https://getartcraft.com/apps/wordcraft) からインストーラーをダウンロード。
2. インストーラーを実行してセットアップ。

### ソースからビルド（Rust環境がある場合）
```bash
git clone https://github.com/storytold/wordcraft
cd wordcraft
cargo run --release
```

---

## 4. 主な機能 & 活用ポイント

1. **リッチな文書校閲（変更履歴 & コメント）**:
   - 複数人での校閲作業や推敲時に、修正箇所をトラッキングしながらコメントを付与できます。
2. **参考文献・引用管理（References）**:
   - 論文やレポート、技術文書作成に必要な文献リストや脚注の挿入に対応。
3. **差し込み印刷（Mail Merge）**:
   - 宛名ラベルやテンプレート文書の一括生成など、実務向けの差し込み印刷機能を装備。
4. **Markdown では対応しきれない複雑なレイアウト**:
   - 表の細かなセルの結合・罫線設定や、段組、厳密なページ余白・ヘッダー/フッター設定が必要な公的文書・契約書・レポート作成に最適です。

---

## 5. 関連リンク
- 公式ページ: [https://getartcraft.com/apps/wordcraft](https://getartcraft.com/apps/wordcraft)
- GitHub リポジトリ: [storytold/wordcraft](https://github.com/storytold/wordcraft)
