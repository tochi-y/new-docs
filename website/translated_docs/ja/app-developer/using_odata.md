---
id: using_odata
title: OData Service Collection (OSC)の使い方
sidebar_label: OData Service Collection (OSC)の使い方
---

PersoniumのOData Service Collection (OSC)はBox内に作成できるリレーショナルデータを扱うことのできる空間です。
単数または複数のテーブルをつくってデータを管理したり検索したりといったことをOData (v2)プロトコルを通じて行うことができます。

## OSC作成
OSCを使うにはまずBox内の任意の場所にOSCを作成する必要があります。

## スキーマ情報の確認
テーブル定義といったいわゆるスキーマ情報は[スキーマ情報取得API](../apiref/316_User_Defined_Data_Schema.md)で確認できます。
返却されるXMLはEDMXと呼ばれる形式であり、簡単にいえばどんなテーブル、どんなカラムがあり、どのようなリレーションが張られているかという情報を表しています。

当然最初は何もテーブルがない状態でありそのままでは何もデータが登録できません。まずはテーブルを作成してみましょう。

## スキーマ定義
Personiumではスキーマ操作自体もODataのインターフェイスで行います。具体的には対象とするOSCのURLの$metadata以下がスキーマを操作するためのODataの空間となっており、ここに予め用意されているEntityType, Propertyといったスキーマ管理のためのEntitySetを操作することでスキーマを管理します。

## テーブル作成
PersoniumではEntityTypeを作成することでテーブル相当のものが作成できます。　
    [参照](../apiref/345_Create_EntityType.md)

> OData仕様においてはEntityTypeとは本来は型情報であり、それに基づいてEntitySetというテーブル相当のものを作るという考え方となっています。Personiumでは実用性を重視し、EntityTypeを作成することにより同名のEntitySet（テーブル相当概念）を自動作成します。そのためEntityType作成によりテーブルが作成されることとなります。

## プリセットのプロパティ

OSCで作成するテーブルには、自動で単一主キー項目(__id)とEntity(レコード)の作成日時(__created)、更新日時(__updated)が定義されます。
> 独自の（複合）主キー項目を定義する機能は構想としてはありますが未実装です。

## Dynamic Property

ODataのEntityTypeにはOpenTypeという考え方があります。これはスキーマレスDB的な考え方を取り入れたものであり、
現状のPersoniumのEntityTypeはすべてOpenTypeとなります。すなわち、未定義の項目を含むデータ登録リクエストがあったとき、
これを受け入れデータを格納します。

> スキーマ情報(EDMX）上では、EntityType要素のOpenType属性が必ずTrueになるかたちで現れます。このような動作を嫌う利用者のために、OpenType=falseなEntityType（未定義項目の登録はエラーにする）のサポートも予定していますが未実装です。

このようにして格納された項目はODataではDynamicPropertyと呼ばれ、
Personiumではスキーマ上はDeclared=falseという属性のついた未宣言プロパティとして認識され、スキーマ定義上確認も可能です。

> このDeclared属性をあとでtrueに変更する機能も実装を予定していますが未実装です。


DynamicPropertyはアジャイルな開発を支援するための機能で、例えばスキーマ定義としてEntityTypeだけを作成し、PropertyはすべてDynamicにしてしまうという使い方も可能です。

### 現状の制限

現状のPersoniumはスキーマ変更に関して多くの制限がありますのでご注意ください。

* Propertyの更新はできません。
* EntityType削除のためには紐づくPropertyをすべて削除する必要があります。
* Property削除のためにはデータを空にする必要があります。

## アクセス制御

OSC自体にACLを設定することはできますが、現時点のPersoniumでは内部の子リソースに対してのACL設定はできません。
したがって例えばテーブルごとにアクセス権を変えるようなことはできません。
