# Claude Code × Git/GitHub 実践ラーニング

Claude Codeを高度活用するために必要なGit/GitHub知識を、Claude Code操作に直結させながら学べるHTMLアプリ。

## 特徴

- **環境構築不要**: ブラウザで即起動
- **Claude Code連動**: 各コマンドを「Claude Codeでの意味」で解説
- **プロンプト集付き**: 実際に貼り付けられるプロンプト例を掲載
- **PWA対応**: スマホのホーム画面に追加してアプリとして使える

## 学習内容

| レベル | 内容 | 対応するClaude Code操作 |
|---|---|---|
| Lv.1 | git init / コミット / .gitignore | Claude Code起動・CLAUDE.md配置 |
| Lv.2 | ブランチ / GitHub連携 / PR | Worktree / company-developer |
| Lv.3 | Worktree管理 / GitHub Pages / Actions | AI Company並行作業 |

## GitHub Pagesデプロイ手順

```bash
# 1. このリポジトリをフォーク or クローン
git clone https://github.com/[username]/claude-code-git-learning.git

# 2. Settings > Pages > Source: Deploy from a branch > main / root

# 3. デプロイ完了後のURL
# https://[username].github.io/claude-code-git-learning/
```

## ローカルで動かす

```bash
# Python 3 がインストールされていれば
cd claude-code-git-learning
python -m http.server 8000
# http://localhost:8000 で開く
```
