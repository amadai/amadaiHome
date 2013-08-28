# weinreの紹介

## 概要
 
 * __WE__b __IN__spector __RE__mote
 * ワイナー　または　ワイナリー　と読む
 * webkitのInspectorのようなデバッグ機能をリモートで提供してくれる  
 →　スマホで表示しているサイトのDOMなどを、weinreを起動しているPCで確認できる！  
 →　実機でスマホサイトのデバッグができる
 

## 使用手順

### 1.node.jsのインストール
node.jsが必要です。  
[nodejs.org](http://nodejs.org/)からインストールしてください

### 2.weinreのインストール
 node.jsと一緒にインストールされているのnpmを使用します。  
 →　コマンドプロンプト  
 `npm install -g weinre`

### 3.weinreの起動
・自PCのIPアドレスを調べる  
 →　コマンドプロンプト  
 `ipconfig`

・weinre起動  
 →　「-boundHost」 オプションに先ほど調べた自PCのIPアドレスを指定  
 `C:\Users\Owner>weinre -boundHost 192.168.xx.xx`
 `2013-07-03T11:20:24.232Z weinre: starting server at http://192.168.xx.xx:8080`
 
 

### 4.PC側の確認
http://192.168.xx.xx:8080　を開いてweinreの管理画面が表示されていればOK

### 5.サイトHTMLの設定
＜script＞タグ or ブックマークレットを貼り付ける。スクリプトは先程のweinreの管理画面中段にある

 * Target Script
 `<script src="http://192.168.xx.xx:8080/target/target-script-min.js#anonymous"></script>`
 
 * Target Bookmarklet
 `javascript:(function(e){e.setAttribute("src","http://192.168.xx.xx:8080/target/target-script-min.js#anonymous");document.getElementsByTagName("body")[0].appendChild(e);})(document.createElement("script"));void(0);`

のどちらかを張り付ける。

### 6.スマホからの接続確認
 スマホがPCと同じWifiに接続していることを確認して、
 上記手順5.でスクリプトを張り付けたページを表示。


### 7.デバッグ
PCから  
http://192.168.xx.xx:8080/client/#anonymous  
にアクセスするとwebkitoのInspectorと同じような画面が表示されているので同じ要領でデバッグ可能です。

  
## 注意点
 * 実機でデバッグする場合は、PCとスマホが同じネットワーク上にあること。  
 →　スマホの通信が3Gのままだったらダメよ
 
## 利点
 * クライアント端末は、アプリのインストールなどの設定が不要
  
## 問題点
 * サイトのソースにjs読み込みのコードを1行追加しなければならない
 * 一部Inspectorに反映されない項目もあった（DOMの属性変更、@mediaquery．．．etc）
 * 実機の場合、同じネットワーク上にないとダメ
 
## その他のスマホサイト用デバッグツール
 
 * [Adobe Edge Inspect](http://codezine.jp/article/detail/7131)
 * [safari 6 (Mac)](http://blog.webcreativepark.net/2012/09/21-110644.html)
 
## 参考URL
 * [ゆるふわWebデベロッピング](http://hazumu.net/blog/2012/07/10/weinre%E3%81%A8mac%E3%81%A7%E3%82%B9%E3%83%9E%E3%83%9B%E9%96%8B%E7%99%BA%E3%82%92%E6%A5%BD%E3%80%85%E3%81%AB/)
 * [第3回　weinreを使ったiOS／Androidアプリの動作検証](http://gihyo.jp/dev/serial/01/phonegap2/0003)
 * [Weinre でリモートデバッグ](http://d.hatena.ne.jp/watanata2000/20130219/1361271257)
 