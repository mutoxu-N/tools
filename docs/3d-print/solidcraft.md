---
title: SolidCraft
description: Pure Rust製のオープンソース・パラメトリック3D CAD
---

# SolidCraft (パラメトリック3D CAD)

[SolidCraft](https://solidcraft.pro/) は、Pure Rust でスクラッチから開発されているオープンソースのパラメトリック 3D CAD アプリケーションです。  
スケッチ、幾何拘束、フィーチャータイムライン（押し出し、フィレット、シェル等）を備え、デスクトップ（Windows, macOS, Linux）およびブラウザ（WebAssembly）で軽快に動作します。

---

## 1. 概要 & 選定理由

- **Pure Rust 製の軽快動作**: B-rep モデリングカーネルから UI（`egui` + `wgpu`）まで全て Rust で実装されており、起動が高速でメモリ消費が極めて少ない。
- **パラメトリックタイムライン**: 寸法やパラメータを変更すると、モデル全体が自動的に再計算・再構築されます。
- **3Dプリンターへの親和性**: 3Dプリントで標準的に使われる **STL** や **3MF** のほか、高精度な製造データ形式である **STEP (AP242)** や **IGES** のインポート・エクスポートに標準対応。
- **AIエージェント連携（MCP標準搭載）**: Model Context Protocol（MCP）サーバーを内蔵しており、Claude Code などの AI エージェントからパラメータ調整、モデリング、スクリーンショット撮影、エクスポートを自動化できます。

---

## 2. 代替対象 & 比較

| 項目 | SolidCraft | Fusion 360 / SolidWorks | FreeCAD |
| :--- | :--- | :--- | :--- |
| **ライセンス** | オープンソース (Apache-2.0) | 商用プロプライエタリ (サブスク) | オープンソース (LGPL) |
| **言語・基盤** | **Pure Rust** (`egui` + `wgpu`) | C++ / クラウド依存 | C++ / Python / OpenCASCADE |
| **起動速度** | **極めて高速（数秒・即座）** | 重い（1分前後） | 普通（数十秒） |
| **Web動作** | WebAssemblyでブラウザ即時動作 | 不可（簡易ビューアのみ） | 不可 |
| **AI (MCP) 連携** | **標準搭載** | なし | プラグイン等 |

---

## 3. 導入手順 & インストール

### Windows での入手
1. [GitHub Releases](https://github.com/bherbruck/solidcraft/releases/latest) から Windows 用インストーラー（`.msi` または `.exe`）をダウンロード。
2. インストールして起動。

### Web ブラウザで試す
インストール不要で、[SolidCraft Web App](https://bherbruck.github.io/solidcraft/app/) からブラウザ上で即座に利用可能です。

### ソースからビルド（Rust環境がある場合）
```bash
git clone https://github.com/bherbruck/solidcraft
cd solidcraft
cargo run --release -p solidcraft -- --sample
```

---

## 4. 3Dプリントに向けた活用ポイント

1. **STL / 3MF エクスポート**:
   - モデリング完了後、メニューから `Export` → `STL` または `3MF` を選択することで、スライサーソフト（Bambu Studio, PrusaSlicer, Cura 等）に直接取り込めます。
2. **STEP (AP242) による寸法精度の維持**:
   - メッシュポリゴンではなく正確な幾何形状（B-rep）で受け渡したい場合、STEP 形式でエクスポートしてスライサー側でテッセレーションを行うことで、円弧や曲面の仕上がりが極めて滑らかになります。
3. **AI エージェントによるパラメータ自動調整 (MCP)**:
   - ヘッドレス CLI モードで MCP を起動し、寸法公差の調整や部品バリエーションの自動出力を AI に指示できます。
   ```bash
   claude mcp add solidcraft -- solidcraft-cli mcp
   ```

---

## 5. 関連リンク
- 公式サイト: [https://solidcraft.pro/](https://solidcraft.pro/)
- GitHub リポジトリ: [bherbruck/solidcraft](https://github.com/bherbruck/solidcraft)
- ドキュメント (The Book): [https://bherbruck.github.io/solidcraft/](https://bherbruck.github.io/solidcraft/)

