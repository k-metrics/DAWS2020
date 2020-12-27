データ分析勉強会2020
================

## 分析大会用データについて

### 集計データ

集計データは、[厚生労働省のオープンデータ](https://www.mhlw.go.jp/stf/covid-19/open-data.html)
を用います。詳細は当該のページで確認してください。

　

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
を参照してください。加工データについては以下の通りです。

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
| pref               | String     | `detectedPrefecture` の日本語                                                                    |
| region             | String     | 八地方区分                                                                                        |
| population         | Numeric    | H30年時点の推計情報（単位は千人、出典：統計局）                                                                    |

　  
なお、オリジナルデータをRを用いて直接読み込みたい場合には、以下のコードを利用してください（表示の都合上、URLを分割しています）。

``` r
library(tidyverse)
library(jsonlite)
"https://raw.githubusercontent.com/reustle/covid19japan-data/master/" %>% 
  paste0("docs/patient_data/latest.json") %>% 
  jsonlite::fromJSON()
```

　

### その他データ

その他、関連データは以下から入手可能です。

  - [都道府県地方区分ならびに推計人口](https://gist.github.com/k-metrics/9f3fc18e042850ff24ad9676ac34764b)
  - [新型コロナウイルス対策病床オープンデータ](https://docs.google.com/spreadsheets/d/1u0Ul8TgJDqoZMnqFrILyXzTHvuHMht1El7wDZeVrpp8/edit#gid=0)

　

## 注意事項

  - 各データは予告なく内容などが変更される場合があります
  - 各データはその内容を保証していません
  - 各データの著作権などは原著作者にあります

　

-----

CC 4.0 BY-NC-SA, Sampo Suzuki
