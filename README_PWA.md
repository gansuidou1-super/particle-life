# Particle Life を PWA(アプリっぽくインストール)にする手順

ローカルでファイルをダブルクリックして開くだけでは、Service Worker が動かないため
「ホーム画面に追加してアプリのように使う」ことはできますが、オフラインキャッシュ機能は
有効になりません。ちゃんとしたPWAにするには、どこかにHTTPSでホスティングする必要があります。

一番簡単なのは **GitHub Pages**(無料)です。

## 手順(GitHub Pages)

1. GitHubで新しいリポジトリを作る(例: `particle-life`)
2. この4つのファイルを全部アップロードする
   - `particle_life.html`(できれば `index.html` にリネームすると URL がすっきりします)
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
3. リネームした場合は `manifest.json` の `start_url` を `"./index.html"` → `"./"` に変更
4. リポジトリの Settings → Pages → Branch を `main` に設定して保存
5. 数分待つと `https://ユーザー名.github.io/particle-life/` でアクセスできるようになる

## インストール方法

- **スマホ(Android Chrome)**: そのURLを開くと「ホーム画面に追加」の案内が出ます。または右上メニューから「アプリをインストール」
- **iPhone(Safari)**: 共有ボタン → 「ホーム画面に追加」
- **PC(Chrome / Edge)**: アドレスバー右側のインストールアイコンをクリック

インストール後はアイコンをタップするだけでフルスクリーンのアプリとして起動し、
2回目以降はオフラインでも動きます(初回アクセス時にキャッシュされるため)。

## 他の選択肢

Netlify や Vercel にドラッグ&ドロップでアップロードする方法でも同様にHTTPSで
ホスティングできます。GitHub Pagesより設定はさらに簡単です。
