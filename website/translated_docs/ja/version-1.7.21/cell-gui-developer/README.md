---
id: version-1.7.21-README
title: Cell GUI開発者向けガイド
sidebar_label: Cell GUI開発者向けガイド
---

CellのGUIを開発したい人向けのドキュメントです

## CellのGUI
Personium は原則全機能をAPIで提供するPDSですが、例外的にGUIを使えるような設定ができる部分が３点あります。

1. Cell URLへのGET （Content-Typeとしてapplication/jsonが設定のないとき）
1. OAuth2.0認可エンドポイント
1. 認可エンドポイントでのパスワード強制変更画面

これらGUIはUnit運用者のブランディングでカスタマイズすべき部分として、後述方法で任意のHTMLを設定可能です。

## 設定の方法

Unitレベルでの一律の設定と、Cell単位での個別設定が可能です。  
Cell単位の設定が優先され、Cell単位設定がない場合Unitレベルの設定が使われます。  

||Unit 設定|Cell設定|備考|
|:--|:--|:--|:--|
|[Cell URLへのGET](../apiref/200_Cell_Root.md)|cell.relayhtmlurl.default|p:relayhtmlurl||
|[認可エンドポイント](../apiref/292_OAuth2_Authorization_Endpoint.md)|cell.authorizationhtmlurl.default|p:authorizationhtmlurl||
|[パスワード変更](../apiref/292_OAuth2_Authorization_Endpoint.md)|cell.authorizationpasswordchangehtmlurl.default|p:authorizationpasswordchangehtmlurl||


## サンプルGUI

GUIのサンプルはプロジェクトで配布しています。  
配布しているものをほぼそのまま使いつつ、見た目（ブランディング）のみを変更することも可能です。  

[ホームアプリ](https://github.com/personium/app-cc-home)


