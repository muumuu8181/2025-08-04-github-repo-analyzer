# GitHub Repository Analyzer

GitHubリポジトリの統計情報を視覚的なHTMLレポートで表示するツールです。

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.6+-blue.svg)

## 概要

- **作成日**: 2025-08-04
- **目的**: GitHubリポジトリの統計を美しいHTMLレポートで可視化
- **使用技術**: Python, GitHub CLI, Chart.js

## 特徴

- 📊 **総合統計**: リポジトリ数、サイズ、言語別分布など
- 📈 **グラフ表示**: Chart.jsを使用した美しいビジュアライゼーション
- 📝 **行数推定**: サンプリングに基づくコード行数とファイル数の推定
- 🌐 **任意ユーザー対応**: 自分以外のGitHubユーザーの分析も可能
- 🎨 **レスポンシブデザイン**: モバイルでも見やすいレイアウト
- ⏱️ **実行時間表示**: 処理にかかった時間を表示

## セットアップ

1. リポジトリをクローン:
```bash
git clone https://github.com/muumuu8181/2025-08-04-github-repo-analyzer.git
cd 2025-08-04-github-repo-analyzer
```

2. 依存関係をインストール:
```bash
pip install -r requirements.txt
```

3. 実行:
```bash
python src/main.py
```

## 使い方

### 基本的な使い方

現在のユーザーの分析:
```bash
python src/main.py
```

特定ユーザーの分析:
```bash
python src/main.py torvalds
```

### オプション

行数カウントのサンプル数を指定:
```bash
python src/main.py --sample 10
```

全リポジトリで詳細分析:
```bash
python src/main.py --sample 999
```

行数カウントを無効化（高速）:
```bash
python src/main.py --sample 0
```

### Windows用バッチファイル

プロジェクトルートに `analyze.bat` を作成:
```batch
@echo off
cd /d "%~dp0"
python src/main.py %*
```

## 出力ファイル

- `github_report_[username]_[timestamp].html` - ビジュアルレポート
- `github_data_[username]_[timestamp].json` - 生データ

## レポート内容

### 統計情報
- 総リポジトリ数
- パブリック/プライベート数
- 総サイズ (MB)
- 推定総行数
- 推定ファイル数
- フォーク数
- アーカイブ済み数

### グラフ
- 月別リポジトリ作成数（棒グラフ）
- 言語別リポジトリ数（ドーナツチャート）
- 言語別推定行数（棒グラフ）

### リスト
- 最新のリポジトリ（10件）
- 最大サイズのリポジトリ（10件）

## 必要要件

- Python 3.6以上
- [GitHub CLI](https://cli.github.com/) (gh)
- GitHub CLIでのログイン済み

### GitHub CLIのインストール

```bash
# Windows
winget install --id GitHub.cli

# Mac
brew install gh

# Linux
sudo apt install gh
```

### GitHub CLIでログイン
```bash
gh auth login
```

## メモ

- API制限を考慮して、リクエスト間に0.5秒の遅延を設定
- 行数推定は言語別の平均バイト/行に基づく推定値
- プライベートリポジトリは他ユーザー分析時は自動除外

## ライセンス

MIT License

## 作者

[@muumuu8181](https://github.com/muumuu8181)