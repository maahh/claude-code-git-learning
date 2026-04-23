# CLAUDE.md — Claude Code × Git/GitHub 実践ラーニング アプリ仕様書

## アプリ概要

- **名称**: Claude Code × Git/GitHub 実践ラーニング
- **コンセプト**: Claude Codeで必要なGit/GitHub知識を、Claude Code操作に対応させながら学べるHTMLアプリ
- **ターゲット**: 非エンジニア・PRレベルの知識あり・Claude Codeを高度活用したい人
- **販売方法**: note（980〜1,480円 買い切り）/ GitHub Pagesでデモ公開

---

## 技術仕様（制約）

- 単一HTMLファイル（index.html）で完結
- 外部API不使用（CDNは可: Font Awesome, Google Fonts等）
- localStorage で進捗保存
- PWA対応: manifest.json + service-worker.js
- ホスティング: GitHub Pages（無料）

---

## ファイル構成

```
index.html          # メインアプリ（全学習コンテンツ）
manifest.json       # PWA設定（アイコン・テーマカラー・スタンドアロン設定）
service-worker.js   # オフラインキャッシュ
README.md           # GitHub Pages説明・デプロイ手順
```

---

## 学習コンテンツ構成（3レベル × 5ステップ = 計15ステップ）

### Lv.1 — Claude Code基本動作に必須（5ステップ）

1. **リポジトリとは何か** — Claude Codeが認識する「プロジェクトの箱」の概念
2. **`git init`** — Claude Codeが動く場所を作る
3. **`git add` / `git commit`** — 作業をスナップショット保存（「元に戻せる状態」を作る）
4. **`.gitignore`** — Claude Codeに見せてはいけないファイルを隠す（APIキー等）
5. **`git status` / `git log`** — 現在の状態と履歴を確認する

### Lv.2 — Claude Code中級活用（5ステップ）

1. **ブランチとは何か** — Worktreeの前提知識（並行作業の基盤）
2. **GitHub リポジトリの作成** — `gh repo create` でクラウドに保存場所を作る
3. **`git push` / `git pull`** — クラウドに保存・取得（バックアップ + マルチデバイス）
4. **Pull Request（PR）** — Claude Codeが `/company-developer` で自動作成する成果物を理解する
5. **WorktreeとBranchの関係** — なぜブランチが必要かを体感で理解する

### Lv.3 — Claude Code高度活用（5ステップ）

1. **Worktreeを使った並行作業管理** — 複数のAIタスクを同時に走らせる
2. **GitHub Pagesでの無料デプロイ** — HTMLアプリを無料公開する
3. **GitHub Actions入門** — Claude Code Hooksとの連携で自動化する
4. **複数Worktreeのマージ戦略** — AI Companyの並行作業を統合する
5. **GITHUB_TOKENの管理** — APIキーを安全に扱う方法

---

## 各ステップのUI構成（要件）

各ステップは以下の要素で構成する:

```
[ステップタイトル]
[解説テキスト（200〜400字）]
[コマンド例（コードブロック）]
[「Claude Codeでの意味」解説ボックス（背景色で強調）]
[実際に使えるプロンプト例（クリックでコピー）]
[理解チェッククイズ（3択、正解で次へ進める）]
[完了ボタン（localStorageに進捗保存）]
```

---

## UIデザイン要件

- **テーマ**: ダーク（Claude Codeユーザー向け）
- **カラーパレット**:
  - 背景: `#0d1117`（GitHub風ダーク）
  - アクセント: `#58a6ff`（青）
  - 成功: `#3fb950`（緑）
  - テキスト: `#c9d1d9`
- **レイアウト**:
  - 左サイドバー: レベル・ステップ一覧（デスクトップ）
  - メインエリア: 学習コンテンツ
  - 上部: 進捗バー（何%完了したか）
- **モバイル対応**: レスポンシブ（PWAのため必須）
- **フォント**: 日本語フォント（Noto Sans JP等のCDN）

---

## 進捗管理（localStorage）

```javascript
// 保存キー
'cggl_progress': {
  level: 1,          // 現在のレベル (1-3)
  step: 3,           // 現在のステップ (1-5)
  completed: [       // 完了したステップ
    {level: 1, step: 1},
    {level: 1, step: 2}
  ],
  quizResults: {}    // クイズの正解記録
}
```

---

## PWA設定

```json
// manifest.json
{
  "name": "Claude Code × Git/GitHub 実践ラーニング",
  "short_name": "CC-Git学習",
  "theme_color": "#0d1117",
  "background_color": "#0d1117",
  "display": "standalone",
  "start_url": "/"
}
```

---

## 開発優先順位

1. index.html のLv.1コンテンツ + 基本UI（Day 1）
2. Lv.2コンテンツ + 進捗管理機能（Day 2）
3. Lv.3コンテンツ + プロンプトチートシート（Day 3）
4. PWA対応（manifest.json + service-worker.js）（Day 4）
5. デザイン最終調整 + レスポンシブ（Day 5）
6. GitHub Pagesデプロイ（Day 6）

---

## 販売戦略

- **デモURL**: GitHub Pages（無料）でLv.1のみ公開
- **購入後**: Lv.2・Lv.3のロック解除コード or フルバージョンをzip配布
- **価格**: 980円（note）→ 1,480円（値上げ予定）
- **差別化**: Claude Code操作に直結・環境構築不要・インタラクティブ体験
