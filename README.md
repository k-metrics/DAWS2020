データ分析勉強会2020
================

## 分析大会について

今回の分析大会は成果を競い合う場ではなく、今まで学んだことをベースとして集計データと個票データの扱いを実習を通して学ぶ場にしたいと考えています。なお、分析に利用する環境・ツールは限定しません。

  - 表計算ソフト（Excelなど）
  - BIツール（Microsoft PowerBI / Exploratoryなど）
  - R（Google Colab / Rcmdr / RStduioなど）/ Python など

　

### 実施日程

分析大会は１月と２月の二回に渡り実施しますが、参加しやすいように当初予定から変更して以下の要領で行います。

| 実施月 | テーマ      | 実施内容         | 備考                |
| --- | -------- | ------------ | ----------------- |
| 1月  | 集計データを扱う | 概要説明、実習、成果発表 | ニュースで見るようなグラフを描こう |
| 2月  | 個票データを扱う | 概要説明、実習、成果発表 | さらに一歩進んだフラフを描こう   |

　

### 実施体制

相談しながら進められるように利用するツールや環境を元にチーム分けを行います。Zoomのブレイクアウトセッション機能を利用しチーム単位のブレイクアウトルームにて実習を行います。  
各チームには「ファシリテーター（支援者）」を配置しますが、意思決定は基本的にメンバー間で行ってください。

　

### 実施内容

新型コロナウィルスに関する二種類のデータ（集計データ、個票データ）を用いて、累計値・前日差・移動平均などを求め、ニュースでみるようなグラフに可視化してみます。関連するデータと組み合わせて処理することも可能です。様々な観点からデータを処理・可視化してみてください。

【例】

  - 陽性者数/PC検査実施人数/重症者/死亡者数の推移や推移比較
  - 単位人口あたりの陽性者数などの比較
  - 属性水準ごとの陽性者数などの推移比較
  - 集計データと個票データの集計結果の比較

　

### 成果発表

成果発表のフォーマットは任意とします。今回の分析大会は前述の通り分析成果を競い合う場ではなく、チーム実習を通して学ぶ場と考えています。したがいまして、発表に関しては自分たちで設定したゴールに至らずとも

  - 苦労した点
  - 分からなかった点
  - 難しかった点
  - 気づいた点

などを発表してください。何かしらのアウトプットを出しましょう。

　

## 分析対象データについて

集計データと個票データは、以下の指定データを利用します。それ以外の関連データは何を使っても構いませんが出典を明らかにしてください。

　

### 集計データ

集計データは、[厚生労働省のオープンデータ](https://www.mhlw.go.jp/stf/covid-19/open-data.html)
を用います。厚生労働省のオープンデータは基本的に前日までの集計結果を下記のような分類で公開していますが、集計方法が単日であったり累計（累積）であったりしますので、注意書きをよく読んでください。

| データ             | 特記                        |
| --------------- | ------------------------- |
| 陽性者数            | 単日                        |
| PCR検査実施人数       | 当日と前日の累積人数の差を当日の実施人数として計上 |
| 入院治療等を要する者の数    |                           |
| 退院又は治療解除となった者の数 |                           |
| 死亡者数            |                           |
| PCR検査の実施件数      | 暫定値であり後日変更される可能性あり        |
| 重症者数            |                           |

　  
なお、各データ詳細は上記のリンクからご確認ください。

　

### 個票データ

個票データは、[Covid19 Japan](https://covid19japan.com/) が GitHub で公開している
[JSON形式の個票データ（CC
BY-NC 4.0）](https://github.com/reustle/covid19japan-data/tree/master/docs/patient_data)
のデータを加工した以下の形式のデータ（CSV形式・UTF-8）を用います。ファイルは Google Drive にも格納します。

    ##    patientId       date gender detectedPrefecture patientStatus   knownCluster
    ## 1         15 2020-01-15      M           Kanagawa     Recovered           <NA>
    ## 2       TOK1 2020-01-24      M              Tokyo     Recovered           <NA>
    ## 3       TOK2 2020-01-25      F              Tokyo     Recovered           <NA>
    ## 4         18 2020-01-26      M              Aichi          <NA>           <NA>
    ## 5         19 2020-01-28      M              Aichi  Hospitalized           <NA>
    ## 6         20 2020-01-28      M               Nara          <NA>           <NA>
    ## 7       HKD1 2020-01-28      F           Hokkaido    Discharged           <NA>
    ## 8       OSK1 2020-01-29      F              Osaka  Hospitalized           <NA>
    ## 9          1 2020-01-30      M        Unspecified    Discharged Charter Flight
    ## 10        23 2020-01-30      M                Mie     Recovered           <NA>
    ##    confirmedPatient    residence ageBracket     pref     region population
    ## 1              TRUE         <NA>         30 神奈川県   関東地方       9177
    ## 2              TRUE Wuhan, China         40   東京都   関東地方      13822
    ## 3              TRUE Wuhan, China         30   東京都   関東地方      13822
    ## 4              TRUE Wuhan, China         40   愛知県   中部地方       7537
    ## 5              TRUE Wuhan, China         40   愛知県   中部地方       7537
    ## 6              TRUE         Nara         60   奈良県   近畿地方       1339
    ## 7              TRUE Wuhan, China         40   北海道 北海道地方       5286
    ## 8              TRUE        Osaka         40   大阪府   近畿地方       8813
    ## 9              TRUE Wuhan, China         50     <NA>       <NA>         NA
    ## 10             TRUE          Mie         50   三重県   近畿地方       1791

　  
オリジナルデータのデータフォーマットについては
[こちら](https://github.com/reustle/covid19japan-data/blob/master/README_data_format.md)
を参照してください。加工データのフォーマットは下記の通りです。

| 列名（変量名）            | データ形式      | 説明                                                                                           |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------- |
| patientId          | String     | 陽性判定者の識別情報（厚生労働省のIDとは異なる）                                                                    |
| date               | YYYY-MM-DD | 陽性判定の報告日（検査日ではない）                                                                            |
| gender             | String     | 陽性者の性別（非公開あり）                                                                                |
| detectedPrefecture | String     | 報告主体（都道府県ならびに空港検疫など）                                                                         |
| patientStatus      | String     | 陽性者の状態（[詳細](https://github.com/reustle/covid19japan-data/blob/master/README_data_format.md)） |
| knownCluster       | String     | 陽性者のクラスタに関する情報                                                                               |
| confirmedPatient   | boolean    | FALSEの場合は重複報告などの可能性あり                                                                        |
| residence          | String     | 陽性者の居住地（非公開あり）                                                                               |
| ageBracket         | Numeric    | 陽性者の年代（非公開あり）                                                                                |
| pref               | String     | `detectedPrefecture` の日本語都道府県名                                                               |
| region             | String     | 都道府県の八地方区分名                                                                                  |
| population         | Numeric    | H30年時点の推計人口（単位は千人、出典：統計局）                                                                    |

　  
なお、オリジナルデータをRを用いて直接読み込みたい場合には、以下のコードを利用してください（表示の都合上、URLを分割しています）。

``` r
library(tidyverse)
library(jsonlite)
"https://raw.githubusercontent.com/reustle/covid19japan-data/master/" %>% 
  paste0("docs/patient_data/latest.json") %>% 
  jsonlite::fromJSON()
```

　

### その他データ

関連データは以下から入手可能です。その他、任意のデータを利用することも可能です。

  - [都道府県地方区分ならびに推計人口](https://gist.github.com/k-metrics/9f3fc18e042850ff24ad9676ac34764b)
  - [新型コロナウイルス対策病床オープンデータ](https://docs.google.com/spreadsheets/d/1u0Ul8TgJDqoZMnqFrILyXzTHvuHMht1El7wDZeVrpp8/edit#gid=0)

　

## 注意事項

  - 各データは予告なく内容などが変更される場合があります
  - 各データはその内容を保証していません
  - 各データの著作権などは原著作者にあります

　

Enjoy\!

-----

CC 4.0 BY-NC-SA, Sampo Suzuki
