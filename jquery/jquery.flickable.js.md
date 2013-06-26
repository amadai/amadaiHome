# jquery.flickable.js の紹介

___

## 概要
 * jqueryプラグイン
 * マウスのフリック操作でスマフォみたいにスクロールできるようになる
 * スマフォでも使える
 * __Android2.xにおける、`overflow:auto`が効かないバグにも対応可能__
 
 ___
 
## スクロールしたいとき

 →　ブロック要素に`overflow: scroll;` `overflow: auto;` などのスタイルを適用  
 &nbsp;
 
`<div style="overflow: visible;">`
<div style="height: 250px;">
<div style="width: 100px; height: 150px; overflow: visible; border: solid 1px #999; float:">
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
</div>
</div>
<br style="clear: both;" />

`<div style="overflow: hidden;">`
<div style="width: 100px; height: 150px; overflow: hidden; border: solid 1px #999; float:">
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
</div>
<br style="clear: both;" />

`<div style="overflow: scroll;">` &nbsp; `<div style="overflow: auto;">`
<div style="float:left; overflow: hidden;">
<div style="width: 100px; height: 150px; overflow: auto; border: solid 1px #999; margin-right: 20px;">
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
x
<br />
</div>
</div>
<br style="clear: both;" />

 [サンプルoverflow](http://test.flak.jp/amasaki/sample_overflow.html)
 
## Android2.xでは全て`overflow: hidden;` になってしまう！
 
 →　自前のjsで実装しましょう。
 
 →　jquery.flickable.js のような便利なプラグインがあるよ。
 
 [DEMO](http://lagoscript.org/jquery/flickable/demo)
 
___

## 参考URL
 * [配布元](http://lagoscript.org/jquery/flickable)
 * [jQuery.flickableがうまく動かないときの対処法](http://utatane.littlestar.jp/tut/archives/68)
 