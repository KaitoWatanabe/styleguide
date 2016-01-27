# HTML/CSS (SCSS) スタイルガイド

# 共通
## プロトコル
### 初級
httpやhttpsを省略しない

### 中級
httpやhttpsを省略する

```html
<!-- 初級 -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- 中級 -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>


```

```css
/* 初級 */
.example {
  background: url(http://www.google.com/images/example);
}
/* 中級 */
.example {
  background: url(//www.google.com/images/example);
}
```

### なぜ？
初級ではファイルを開いて開発する場合に動かないことを防ぐため省略しない。
中級では、githubやherokuなどでhttpsでデプロイした際に動くようにするため。ただし、事前にプロトコルの説明をすること。またタイプ数を減らすため。

## インデント
2スペース。tabインデントは使わない

### なぜ？
github等で共有した際にインデントがずれるのを防ぐため。

## 大文字小文字
タグ名や色番号などすべて小文字を使う。

```html
<!-- Not recommended -->
<A HREF="/">Home</A>

<!-- Recommended -->
<img src="google.png" alt="Google">
```

```css
/* Not recommended */
color: #E5E5E5;
/* Recommended */
color: #e5e5e5;
```

### なぜ？
タイプ数を減らすため。

# HTML

## Document Type
HTML5を使う

```html
<!-- Not recommended -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<!-- Recommended -->
<!DOCTYPE html>

```

### なぜ？
HTML5のAPI等も使えるようにするため。

## クォーテーション
ダブルクオート("")を使う

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>
<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

### なぜ？
W3Cが推奨。

## article,section,nav,aside,header,footer,main
[参考](http://scene-live.com/page.php?page=12)

# CSS
## IDやclass名
### 意味のある名前に
意味のある名前にする。意味のない名前や見た目を表す名前にしない。

```
/* Not recommended: 意味が無い */
#abc123 {}
/* Not recommended: 見た目を表す */
.blue-button {}

/* Recommended: 意味がある */
#about {}
.primary-button {}
```

#### なぜ？
どこのセレクターかわかりやすくするため。また、色等の変更があっても対応するため。

### 命名スタイル
チェーンケース(-でつなぐ)をつかう。また略称を積極的につかう。
しかし、一般的でない略称は用いない。

```
/* Not recommended 略称を使ってない */
#navigation {}

/* Not recommended 何の略かわからない */
.atr {}

/* Not recommended チェーンケースをつかっていない */
#key_visual {}
.loginButton {}

/* Recommended: 略称を使っている */
#nav {}

/* Recommended: 略称のないものはそのまま */
.author {}

/* Recommended: チェーンケース */
#key-visual {}
.login-button {}

```

#### なぜ？
タイプ数を減らすために略称を用いる。
cssのプロパティや、htmlのアトリビュートではチェーンケースを用いているため。

## セレクター
IDやクラスを指定する際は、タグを省略する。

```css
/* Not recommended */
ul#example {}
div.error {}

/* Recommended */
#example {}
.error {}
```

### なぜ？
パフォーマンスが下がるため。

## 単位
### 初級
基本pxを用いる。

### 中級
rem?

## 短縮形

### 初級
border以外短縮系は用いない。0の場合も単位をつける。

### 中級
積極的に短縮形を使う。正し、初めて使う場合解説を必ずすること。
小数の0も省略する。色番号(Hex)も省略できるものは省略する

```
/* 初級 */
border: 1px solid #000000;
font-family: palatino, georgia, serif;
font-size: 20px;
line-height: 0.9;
padding-bottom: 20px;
padding-left: 10px;
padding-right: 10px;
padding-top: 0px;

/* 中級 */
border: 1px solid #000;
font: 20px/.9 palatino, georgia, serif;
padding: 0 10px 20px;
```

### なぜ？
初級では一貫性を重視するため。(数字には単位がいる。色は6桁で表すなど。)。短縮形は覚えにくいため。
中級ではタイプ数を減らすため。

## セミコロン
省略しない
```
/* Not recommended */
.test {
  display: block;
  height: 100px
}
/* Recommended */
.test {
  display: block;
  height: 100px;
}
```

### なぜ？
プロパティを追加した際に、セミコロン忘れを防ぐため。

## スペース
セレクターの後とプロパティ`:`の後は1スペースあける。

```
/* Not recommended */
h3{
  font-weight:bold;
}

/* Recommended */
h3 {
  font-weight: bold;
}
```
### なぜ？
可読性をあげるため。

## 改行
セレクターと`{`の間で改行しない。セレクターが複数ある場合はセレクター間で改行する。

```
/* Not recommended */
h1,h2,h3
{
  font-weight:bold;
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: bold;
}
```

### なぜ？
可読性をあげるため。

## セパレート
ブロック間は1行あける。
```
/* Not recommended */
html {
  background: #fff;
}
body {
  margin: auto;
  width: 50%;
}

/* Recommended */
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

### なぜ？
可読性をあげるため。

## クォーテーション
### 初級
ダブルクオート("")を使う

### 中級
urlのみ省略

```html
<!-- 初級 -->
@import url("http://www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}

<!-- 中級 -->
@import url(//www.google.com/css/maia.css);

html {
  font-family: "open sans", arial, sans-serif;
}
```

### なぜ？
初級では一貫性を重視。
中級ではタイプ数を減らすため。

#SCSS

## 変数名

## ネスト















