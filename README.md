# angular_test

# Setup
1. Node.jsのインストール
2. Angular CLIをインストール
3. ワークスペースを作成してみる
4. 起動する
5. 実装してみる

## 1. Node.jsのインストール

https://qiita.com/sefoo0104/items/0653c935ea4a4db9dc2b

14.17.5 LTS版をダウンロード
https://nodejs.org/ja/

## 2. Angular CLIをインストール
```
npm install -g @angular/cli
```

## エラー
```
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
npm WARN deprecated har-validator@5.1.5: this library is no longer supported
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
npm WARN checkPermissions Missing write access to /usr/local/lib/node_modules
npm ERR! code EACCES
npm ERR! syscall access
npm ERR! path /usr/local/lib/node_modules
npm ERR! errno -13
npm ERR! Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!  [Error: EACCES: permission denied, access '/usr/local/lib/node_modules'] {
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/local/lib/node_modules'
npm ERR! }
npm ERR!
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR!
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator.

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/betashort/.npm/_logs/2021-08-16T12_40_54_546Z-debug.log
```

### 管理者権限で実行する。

```
sudo npm install -g @angular/cli
```

## 3. ワークスペースを作成する
```
ng new {work-space}
```

## 4. 起動してみる
```
ng serve --open
```

# Angularとは

# TypeScript

# build
```
ng build
```

# Projectの3のファイル
1. index.html
2. main.ts
3. styles.scss

## index.html
```html
<app-root></app-root>
```

<app-root>というコンポーネントを表示するためのタグ

## main.ts

### import
```ts
import {読み込む部品} from ライブラリ;
```
ライブラリは、読み込むファイル名+パスを記述する。ただし、読み込むファイルはTypeScriptになるので、拡張子は省略可能。


## app.component
### app.component.html
コンポーネントのHTMLでは、コンポーネントとして表示するタグだけを記述する。

### app.component.ts

#### @Componentデコレータ
タグの名前、テンプレートの場所、スタイルシートの場所を設定する。

#### AppComponentクラス
```ts
export class AppComponent {
  title = 'angular-app';
}
```
exportは、外部から'AppComponent'を使えるようにするためのもの。

# Componentを作成する

```
ng generate component {name}
```

# コンポーネント
アプリケーションを組み立てる構成要素  
`@Component()`デコレータには、次のAngular固有の情報を指定する。
1. コンポーネントがテンプレートでどのように使用されるかを定義するCSSセレクター。このセレクターに一致するテンプレート内のHTML要素はコンポーネントのインスタンスになる。

2. コンポーネントのレンダリング方法をAngularに指示するHTMLテンプレート

3. テンプレートのHTML要素の外観を定義するCSSスタイルのオプションのセット。

コンポーネントは3つのお要素で構成される。
1. データと機能を扱うコンポーネントクラス
2. UIを決定するHTMLテンプレート
3. ルック安堵フィールを定義するコンポーネント固有のスタイル


angular.jp/start


```html
<h2>Products</h2>
<div *ngFor="let product of products">
</div>
```

`*ngFor`を使うと、繰り返し実行される。

プロパティバインディング`[]`構文を用いる。

`*ngIf`を使うと、場合分けが実行される。

`<button (click)="method()"`でイベントバインディング。

`@Component()`は、セレクター、テンプレート、スタイルなど、コンポーネントに関するメタデータを提供する。

# コンポーネントの概要

* ページに表示するものを宣言するHTMLテンプレート
* 振る舞いを定義するTypescriptクラス
* テンプレート内でコンポーネントがどのように使用されるかを定義するCSSセレクター
* オプションで、テンプレートに適用されるCSSスタイル

## コンポーネントの作成

### 自動で作成する
`ng generate componet <componet-name>`

### 手動で作成する。
* <component-name>.component.ts

```TypeScript
import { Component } from '@angular/core';
//デコレータ
@Component({
  //セレクタを指定する。
  selector: 'app-component-overview',
  //HTMLテンプレート
  templateUrl: './component-overview.component.html',
  //テンプレートのスタイル
  styleUrls: ['./component-overview.component.css']
})
//コンポーネントのコードを含むclassを追加する。
export class ComponentOverviewComponent{
}
```

```TypeScript
@Component({
  selector: 'app-component-overview',
  template: '<h1>Hello World!</h1>',
  styles: ['h1 { font-weight: normal; }']
})
```
