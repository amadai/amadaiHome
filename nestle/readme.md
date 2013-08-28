﻿#ネスレメルマガ　コーディング方法まとめ

##概要
* ALTはレギュレーションに沿って設定する
* Hotmailで受信した時に、リンク画像の下に勝手にマージが設定されてしまうので、
コーディングで工夫する。
 ※Outlookで配信してHotmailで受信した場合のみ発生


## スライス
※以下は、Fireworksを使用した例です。

### 画像リンクは門型スライスで
リンクがつくところの画像は下に5px以上の隙間ができるようにスライスする。
 > hotmailで受信した時に、画像リンクに謎のマージンがつくため
![門型スライス例](./img/slice.jpg)
※デザインの時点で、リンク画像の下部にはベタ背景のみを引くように注意する。
※テキストリンクの場合は問題ない。
（文字、画像、グラデーションが重ならないデザインにすること。）

### リンクとALTの設定
リンク画像には指定のURLとALTを設定する。
targetは全て”_blank”に設定する。

### 画像の最適化
 「最適化」パネルでjpgの圧縮率を設定する。
 （書き出し画像の合計サイズが 1MB以下 で最大になるように調整）


## 書き出し
スライスができたら、書き出し（Alt + Ctrl + R）する。
設定のポイントは
 * ファイル名　→　”index.html”指定
 * HTML　→　HTMLファイルの書き出し
 * スライスのない領域も含める　→　チェックを外す
 * サブフォルダーに画像を置く　→　チェックを入れる
 * サブフォルダ　→　”out_images”指定（書き出すHTMLを同じ階層に作成しておく）
![書き出し設定](./img/output.jpg)


## コーディング
※以下はDreamweaverを使用した例です。
 * 文字コードを「S-JIS」に設定
  修正　→　ページプロパティ（Ctrl + J）　→　タイトル/エンコーディング
  エンコーディング（E）で”日本語(シフト JIS)”選択
  
 * ＜titile＞設定
  - （例）ネスレアミューズからのお知らせ August
  
 * 基本＜style＞の追加
 `
 <style type="text/css">
  body,div,table,tr,td,th,h1,h2,p,span,a,img{
 	padding: 0;
 	margin: 0;
 	font-size: 9pt;
 	text-align: left;
 	border: none;
 	color: #372E27;
 }
 body,div,table,tr,td,th,h1,h2,p,span,a,img{
 	line-height: 68%;
 }
 td{
 	vertical-align: top;
 }
 a:visited {
 	color: purple;
 }
 a,
 a:visited,
 a:hover {
 	color: #1271C3;
 }

 td img {display: block;}
 table {
 	display: block !important;
 }
 </style>
 `
 
 *「 画像が上手く表示されない方は～」リンク設定
  （例）＜table＞タグ直下に行を追加
  `
  <tr bgcolor="#ffffff">
   <td height="22" style="font-size:10pt; line-height:1; text-align:center;"><a class="fc_1" href="http://magazine.nestle.co.jp/shop/130828bddm/index_webup.html" target="_blank" style="font-size:10pt; line-height:1.4 !important;">※画像が上手く表示されない方は、こちらをクリックしてください。</a></td>
  </tr>
  `
 * ＜table＞タグのスタイル変更
  "display: inline-table;"　→　"display: block !important;"
  
 * ページ全体の中央寄せ
  （例）左右マージンを”auto”に
  
 * 画像リンク下のすき間画像削除
  書き出し時に、「スライスのない領域も含める」のチェックを外していれば
  画像リンク直下のスライスを設定しなかった箇所が「spager.gif」に自動で置き換わっているので
  それを目印に「spacer.gif」を含む＜td＞タグごと削除する。
  （空の＜tr＞タグだけが残る状態）
  
 * amp;の削除
  URL中に「&」が入っている場合、Fireworksで書きだした際に「&amp;」に自動変換されるが、
  メルマガ配信時に文字化けするため、「&amp;」→「&」に変更しておく。


## レギュレーションチェック
 別添資料の「YYMMDDddm_チェックリスト.xls」を参考にALTテキストのレギュレーションをチェックする。


## 配信テスト
 outlookを使ってテスト用のアドレスに配信し、Webメール等で表示にくずれがないかチェックする。
 ※2031年2月ごろ、Outlook.comの開始に伴いHotmailの仕様が変更されたため
 正確に表示の確認ができなくなったが、今まで通りのコーディング方法で問題ないとのこと。
 Thunderbirdなどの他のメーラでの受信チェックのみ行っています。


## 提出用ファイルセット
 作成するファイルは3種類
 * index_local.html　→　制作者確認用
 * index.html　→　配信用
 * index_webup.html　→　「画像がうまく表示されない方は～」リンクから飛んでくるWEBサイト掲載用

### index_local.html
 Fireworksから書き出して、上記修正を施したもの。
 画像パスは相対パスで記述されている。

### index.html
 index_local.htmlをメール配信用に修正したもの。
 画像パスは絶対パスで記述。
 パスは毎回変更になりますが、ある程度のルールはあって
  （例） src="http://magazine.nestle.co.jp/shop/130828ddm/out_images/index_r1_c1.jpg"
  上記の”/130828ddm/”の数字の部分が配信日になっていてそこだけが変更になりるのが慣例です。
  
 ** ABテストがある場合 **
 ABテスト（後述）がある場合は
 （例）
 【Aファイル】 src="http://magazine.nestle.co.jp/shop/130828addm/out_images/index_r1_c1.jpg"
 【Bファイル】 src="http://magazine.nestle.co.jp/shop/130828bddm/out_images/index_r1_c1.jpg"
 配信日と”ddm”の間に”a”又は”b”が入ります。

### index_webup.html
 index.htmlから「見えない方はこちら～」リンクを削除したもの。

 ** 差し込みデータ（顧客名等）がある場合 **
 顧客名や所持ポイントなどの差し込みデータがあるメールの場合、
 「#%%MSG02%%#」のような置換文字列が記述されます。
 これは、全てのお客さまが閲覧するindex_webup.htmlの場合不要となるので削除します。
 （削除したことにより前後の画像がずれるので、高さの調整なども必要です）