# libgif-js

ブラウザ上でローカルのGIFファイルを解析し、寸法、再生時間、フレーム数などのメタデータを抽出する軽量なJavaScriptライブラリです。

このプロジェクトは、優れた[jsgif](https://github.com/shachaf/jsgif)プロジェクトをフォークし、解析とメタデータ抽出に特化するようにリファクタリングしたものです。

## 機能

-   **クライアントサイド解析:** ブラウザ内でGIFファイルを直接処理します。サーバーサイドのコードは必要ありません。
-   **メタデータ抽出:** 幅、高さ、アスペクト比、総再生時間、フレーム数を取得します。
-   **PromiseベースのAPI:** 非同期であり、簡単に組み込むことができます。
-   **ESモジュール:** モダンなJavaScriptプロジェクトに簡単にインポートできます。

## デモ

`example.html`にデモが含まれています。実行するには以下の手順に従ってください:

1.  このリポジトリをクローンします。
2.  ローカルのWebサーバーでプロジェクトディレクトリをホストします。
3.  ブラウザで`example.html`を開きます（例: `http://localhost/example.html`）。

**注意:** ブラウザのセキュリティ制限により、ローカルディスクから直接HTMLファイルを開いた場合（`file://...`）、このデモは動作しません。

## インストール

npmからパッケージをインストールします:

```bash
npm install gif-decode
```

## 使い方

`readLocalGIF`関数をインポートし、`File`オブジェクト（通常はファイル入力から取得）を渡します。

```javascript
import readLocalGIF from 'gif-decode';

const fileInput = document.querySelector('input[type="file"]');

fileInput.addEventListener('change', (event) => {
  const file = event.target.files[0];
  if (file) {
    readLocalGIF(file).then((gifInfo) => {
      console.log(gifInfo);
      // 出力例:
      // {
      //   width: 500,
      //   height: 375,
      //   ratio: 1.3333333333333333,
      //   duration: 2500,
      //   length: 25
      // }
    });
  }
});
```

## API

### `readLocalGIF(file)`

GIFのメタデータを含むオブジェクトで解決される`Promise`を返します。

-   **`file`**: GIFファイルを表す`File`オブジェクト。

#### 解決されるオブジェクトのプロパティ

-   `width` (Number): GIFの幅（ピクセル単位）。
-   `height` (Number): GIFの高さ（ピクセル単位）。
-   `ratio` (Number): GIFのアスペクト比（`width / height`）。
-   `duration` (Number): アニメーションの総再生時間（ミリ秒単位）。
-   `length` (Number): GIFの総フレーム数。

## ライセンス

MIT License — 詳細は[LICENSE](LICENSE)を参照してください。
