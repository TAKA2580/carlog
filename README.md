# CarLog PWA — デプロイ手順

## ファイル構成
```
carlog-pwa/
├── index.html     ← メインアプリ
├── manifest.json  ← PWA設定
├── sw.js          ← Service Worker (オフライン対応)
├── icon.svg       ← アプリアイコン
└── README.md      ← この手順書
```

---

## 方法① GitHub Pages（無料・永久）

1. **GitHubアカウントを作成** → https://github.com

2. **新しいリポジトリを作成**
   - 右上の `+` → `New repository`
   - Repository name: `carlog`（なんでもOK）
   - Public を選択
   - `Create repository`

3. **ファイルをアップロード**
   - `uploading an existing file` をクリック
   - 4ファイル（index.html, manifest.json, sw.js, icon.svg）をドラッグ＆ドロップ
   - `Commit changes`

4. **GitHub Pages を有効化**
   - リポジトリの `Settings` タブ
   - 左メニューの `Pages`
   - Source: `Deploy from a branch`
   - Branch: `main` / `(root)` → `Save`

5. **URLを確認**
   - 数分後に `https://ユーザー名.github.io/carlog/` でアクセス可能

---

## 方法② Netlify（無料・より簡単）

1. https://netlify.com でアカウント作成

2. ダッシュボードの **「Add new site」→「Deploy manually」**

3. `carlog-pwa` フォルダをそのままドラッグ＆ドロップ

4. 数秒で `https://xxxxxx.netlify.app` のURLが発行される

---

## スマホのホーム画面に追加（PWA化）

### iPhone (Safari)
1. Safari でアプリのURLを開く
2. 下部の **共有ボタン**（□↑）をタップ
3. **「ホーム画面に追加」** をタップ
4. 名前を確認して **「追加」**

→ ホーム画面にアイコンが追加され、フルスクリーンアプリとして起動します

### Android (Chrome)
1. Chrome でURLを開く
2. 右上メニュー（⋮）→ **「ホーム画面に追加」**
3. または、アドレスバーのインストールアイコンをタップ

---

## オフライン動作について

初回アクセス後、Service Worker がアプリ全体をキャッシュします。
2回目以降はインターネット接続なしで動作します。

## データについて

データはスマホ本体の IndexedDB に保存されます。
- アプリを削除するとデータも消えます
- 設定画面の「JSONエクスポート」で定期的にバックアップを取ることをお勧めします
- 機種変更時は「JSONエクスポート」→ 新しいスマホで「JSONインポート」でデータ移行できます
