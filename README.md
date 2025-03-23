# Astro with Biome and Prettier on Devcontainer
## 環境
- Ubuntu on WSL2
  - Docker
- VSCode
  - `Dev Containers`，`Remote Development`拡張機能をインストール

**参考：[Dev Container on WSL2で開発環境構築](https://zenn.dev/ykdev/articles/14a108290e24f9)**

## プロジェクトの実行方法
ターミナルで`npm run dev -- --host`をするとVSCode画面の右下に`Open In Browser`が出るため，それをクリック

## ディレクトリ構造
- `pages/index.astro`
  - Webページのルート
- `layouts/Layout.astro`
  - ページ全体のレイアウトを調整している
  - `<slot />`があることによって，`pages/index.astro`で`<Layout><Welcome /></Layout>`のように`<Welcome />`を埋め込むことができる
- `components/Welcome.astro`
  - `npm run dev -- --host`したときに表示されるページ

## 使っているライブラリ・フレームワーク
### Astro
- フロントエンドのビルドツール
- テンプレートを作成

### Biome
- リント + フォーマットツール
  - ESLint + Prettierの代替ツール
  - コードを整形してくれる
  - ファイルを保存したときに自動で実行されるようにしている（`.vscode/settings.json`）

### Prettier
- フォーマットツール
- AstroはBiomeのフォーマッタが一部未対応のため，`.astro`ファイルのみPrettierでフォーマットする

### Tailwind CSS
`.css`ファイルを用意せず，HTMLのクラス要素に直接スタイルを当てるためのフレームワーク

## 設定ファイル群
### `.vscode/settings.json`
- タブサイズをスペース2個分に指定

### `.npmrc`
`npm install [library]`したときに，自動でバージョン固定オプション`--save-exact`を追加するように指定

### `.devcontainer/devcontainer.json`
- devcontainerの設定ファイル
- `Node v22`と`GitHub CLI（GitHubの便利ツール）`，`Biome`と`Astro`を自動でインストールするように指定

### `biome.json`
Biomeの設定ファイル

## 初期設定
1. [Dev Container on WSL2で開発環境構築](https://zenn.dev/ykdev/articles/14a108290e24f9)を参考に空ディレクトリをDevcontainerに用意
2. Devcontainerの外（WSL）から[Vite 公式サイト](https://ja.vite.dev/guide/)を参考に`Vite + React + TypeScript`プロジェクト作成
3. [Biome 公式サイト](https://biomejs.dev/ja/guides/getting-started/)を参考にインストール・init
4. [Tailwind CSS 公式サイト](https://tailwindcss.com/docs/installation/using-vite)を参考にインストール
5. [VSCodeでNext.jsのプロジェクトを作成した後にやることメモ(DevContainerとBiome.jsの設定)](https://zenn.dev/ikoamu/articles/e21d9665b6189e)を参考にDevContainerとBiome.jsの設定
6. [package.jsonでのバージョン指定は完全固定にしよう](https://zenn.dev/nekoya/articles/c6057fbb896391)を参考に`.npmrc`ファイル作成