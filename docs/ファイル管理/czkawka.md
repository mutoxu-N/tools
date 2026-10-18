---
title: Czkawka
description: Pure Rust製・超高速な重複ファイル・不要ファイル整理ツール
---

# Czkawka (重複ファイル・不要ファイル整理)

[Czkawka](https://czkawka.org/)（チュカフカ）は、Pure Rust で開発されたオープンソース・高速・多機能なファイル整理・重複クリーンアップツールです。  
高度なマルチスレッド並列処理とキャッシングにより、ディスク内の重複ファイル、類似画像・動画・音楽、空フォルダ、破損ファイルなどを極めて高速に検出・整理できます。

---

## 1. 概要 & 選定理由

- **Pure Rust による圧倒的な検出速度**: メモリ安全性とマルチスレッド並列処理を活かし、膨大なファイル群（数十万〜数百万ファイル）でも他のツールとは比較にならない爆速でハッシュ計算・比較を行います。
- **多彩な重複・不要ファイル検出モード**:
  - **重複ファイル**: サイズ、名前、ハッシュ値（Blake3, SHA256等）による厳密な重複判定。
  - **類似画像・動画・音楽**: 知覚ハッシュ（Perceptual Hashing）を用いて、解像度やフォーマットが異なる同一コンテンツを検出。
  - **空ファイル・空フォルダ**: 肥大化したプロジェクトやバックアップ内の不要な空ディレクトリを一括特定。
  - **破損ファイル・無効リンク**: 壊れた画像・音楽・アーカイブや、リンク切れしたシンボリックリンクを検出。
- **多彩なインターフェース**:
  - 初心者でも使いやすいモダンな **GUI**（Slint / GTK4 版）
  - サーバー運用や自動化スクリプトに組み込める **CLI** 版
  - ターミナル上で操作できる **TUI** 版
- **完全無料・オープンソース & プライバシー保護**: 広告やトラッカー、クラウド送信は一切なく、完全ローカルで安全に動作します。

---

## 2. 代替対象 & 比較

| 項目 | Czkawka | dupeGuru | CCleaner / BleachBit |
| :--- | :--- | :--- | :--- |
| **ライセンス** | オープンソース (MIT) | オープンソース (GPL) | 商用プロプライエタリ / GPL |
| **言語・基盤** | **Pure Rust** (ネイティブ) | Python / Qt | C++ / Python |
| **スキャン速度** | **圧倒的に高速 (並列/Blake3)** | 普通 | 普通 |
| **知覚ハッシュ** | **画像・動画・音楽の類似判定** | 画像・音楽対応 | 非対応 |
| **CLI / 自動化** | **強力なCLI/TUI完備** | 簡易CLI | コマンドライン対応 |
| **プラットフォーム** | Windows, macOS, Linux, Docker | Windows, macOS, Linux | Windows, Linux |

---

## 3. 導入手順 & インストール

### Windows での入手
`winget` または Scoop を利用するのが最も手軽です。

```powershell
# GUI 版のインストール
winget install qarmin.czkawka

# CLI 版のインストール
winget install qarmin.czkawka-cli
```

または [Czkawka 公式サイト](https://czkawka.org/) / [GitHub Releases](https://github.com/qarmin/czkawka/releases) から最新のバイナリをダウンロードして展開します。

### macOS での入手
```bash
brew install czkawka
```

### Linux (Flatpak / Snap)
```bash
flatpak install flathub com.github.qarmin.czkawka
```

---

## 4. 主な機能 & 活用ポイント

1. **写真ライブラリの重複・類似整理**:
   - スマホのバックアップや撮影写真の中で、「連写した似たような構図」や「リサイズされた同一写真」を類似度（Similarity）のスライダー調整で瞬時にリストアップできます。
2. **キャッシュによる2回目以降の高速化**:
   - 一度スキャンしたファイルのハッシュ値はキャッシュされるため、定期的なドライブメンテナンスの時間を大幅に短縮できます。
3. **安全な削除・隔離機能**:
   - 即座に完全削除するだけでなく、「ごみ箱へ移動（Recycle Bin）」や「別フォルダへの隔離移動」、「シンボリックリンク / ハードリンクへの置換」が選択でき、誤削除のリスクを最小限に抑えられます。
4. **CLI による定期バッチ・ヘッドレス運用**:
   - 自宅サーバーや NAS 上のストレージ監視スクリプトに組み込み、空フォルダや重複ファイルを定期レポート化できます。

---

## 5. 関連リンク
- 公式サイト: [https://czkawka.org/](https://czkawka.org/)
- GitHub リポジトリ: [qarmin/czkawka](https://github.com/qarmin/czkawka)
- ドキュメント / マニュアル: [https://github.com/qarmin/czkawka/blob/master/instructions/Instruction.md](https://github.com/qarmin/czkawka/blob/master/instructions/Instruction.md)
