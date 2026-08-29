# STU48 推しペンラサーチ (PWA)

STU48メンバーのペンライトカラーを検索・絞り込みできる非公式ファンメイドツールです。
スマホのホーム画面に追加してアプリのように使えます(PWA対応)。

## GitHub Pagesで公開する手順

1. GitHubで新しいリポジトリを作成する(例: `oshi-penlight-search`)
   - Public / Private どちらでも公開設定は可能ですが、GitHub Pagesを使うにはリポジトリがPublicである必要があります(Freeプランの場合)

2. このフォルダの中身をリポジトリのルートにそのまま置いて push する

   ```bash
   cd oshi-penlight-search
   git init
   git add .
   git commit -m "Initial commit: STU48推しペンラサーチ PWA"
   git branch -M main
   git remote add origin https://github.com/<あなたのユーザー名>/<リポジトリ名>.git
   git push -u origin main
   ```

3. GitHubのリポジトリページで `Settings` → `Pages` を開く

4. `Build and deployment` の `Source` を `Deploy from a branch` にし、
   `Branch` を `main` / `/ (root)` に設定して `Save`

5. 数分待つと `https://<あなたのユーザー名>.github.io/<リポジトリ名>/` で公開される
   (Pages画面上部に公開URLが表示されます)

6. スマホでそのURLを開き、
   - iPhone (Safari): 共有ボタン → 「ホーム画面に追加」
   - Android (Chrome): メニュー → 「アプリをインストール」/「ホーム画面に追加」

   でアプリのようにアイコンから起動できるようになります。

## ファイル構成

```
.
├── index.html          # 本体(検索・絞り込み・お気に入り機能)
├── manifest.json        # PWAマニフェスト(アプリ名・アイコン・テーマカラー)
├── sw.js                 # Service Worker(オフラインキャッシュ)
├── favicon.ico
├── .nojekyll             # GitHub PagesのJekyll処理を無効化
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-512-maskable.png
    └── apple-touch-icon.png
```

## 更新するときは

`index.html` 内の `MEMBERS` 配列を編集してメンバー情報を更新したら、
同じ手順で `git add . && git commit -m "update" && git push` すれば
GitHub Pagesに自動反映されます(数分かかることがあります)。

Service Workerがキャッシュしているため、更新後すぐに反映されない場合は
ブラウザで一度リロード(スマホの場合はアプリを閉じて開き直す)してください。
それでも反映されない場合はキャッシュ名 (`sw.js` 内の `CACHE_NAME`) の
バージョン番号を上げてください(例: `v1` → `v2`)。

## 免責

本ツールは非公式のファンメイドツールです。「STU48」等の名称・商標および
各種権利は各権利者に帰属します。
