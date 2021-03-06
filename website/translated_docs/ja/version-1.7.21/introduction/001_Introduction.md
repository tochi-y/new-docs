---
id: version-1.7.21-001_Introduction
title: Personiumとは何ですか？
sidebar_label: Personiumとは何ですか？
---

Personium(ペルソニアム)はオープンソースのPDS (Personal Data Store) サーバソフトウェアです。  
PDSでは個人を中心にしたデータの管理を行います。

![Personiumとは](assets/Personium.png "Personiumとは")

## Personiumが目指す世界

データを個人中心に置くことで、個人の意思でデータをコントロールし、個人に価値が還元されるようなデータ流通・利活用を目指します。

![Personiumが目指すデータ流通・利活用](assets/personium_aims_for.png)

## Personiumの特長

### 自身でPDSサーバを立てられる

* オープンソースソフトウェアであるため、事業者/自治体/政府/個人等でPDSプロバイダになれます。

### 全機能がREST API

* HTTPはどんなプラットフォーム（OS, 開発言語）でも扱えるため、クライアントのプラットフォームを選びません。
* PDSとしてのGUIはサンプル配布しますが誰でも改造可能です。

### データ開示・共有設定は相手PDSのURLを指定

* PersoniumのPDSには皆URLが与えられます。
* 他者(例： 妻、かかりつけ医、勤務先 etc.)へのデータ開示・共有は相手PDSのURLを指定して行います。
* 他者PDSアクセスには電子署名技術を利用しており、相手は別サーバであっても構いません。

![データ開示・共有設定](assets/DisclosureData.png "データ開示・共有設定")

### Web of PDSを構成可能
* データ開示・被開示という関係で結ばれたPDS群は、特定の事業者が胴元（⇒ 一人勝ち）になるのではない中心を持たないDecentralizedなネットワークを構成します。 （分散ソーシャルグラフ）
* バラバラに建てられたWebサーバにホストされたWebサイトがリンクしあってwwwができたように、バラバラに立てられたPDSがリンクし合った巨大なWeb of PDSを形成可能です。
オープンなエコシステム形成に必要となるセキュリティも実装しています。

### データ権限の移譲が可能

* 受動的データ主体：幼児・高齢者などは、親族等に全データの全権限を許可することでPDSの運用移譲が可能となります。
![受動的データ主体](assets/PassiveDataSubject.png "受動的データ主体")

### データ主体を人に限らず、モノ・組織などに拡張可能

* 受動的データ主体を扱う要領でデータ主体をモノや組織などにも拡張可能です。（例、家族/犬のポチのデータストア）
* IoM, IoT, IoE を統合的に扱うモデルを標榜します。（Cyber-Physical）

![データ主体の拡張](assets/ExpansionDataSubject.png "データ主体の拡張")
