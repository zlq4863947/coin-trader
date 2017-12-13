# coin-trader

## テスト

```
npm test
```

## 仮想通貨の取引

```
npm link
candlestick show
```

## help

```
$ candlestick -h

  Usage: candlestick [options] [command]

  CandlestickのInfluxDBとKapacitorとの管理ツール


  Options:

    -V, --version  output the version number
    -h, --help     output usage information


  Commands:

    show|s [options] [pair]    Continuous Queriesを表示
    upsert|u [options] [pair]  Continuous Queriesを登録/更新
    drop|d [options] [pair]    Continuous Queriesを削除
    task [action]              KapacitorのTaskを登録(更新)/表示/削除
    tick [pair]                tickデータをランダムで登録
    depth [pair]               depthデータをランダムで登録

  
pair: btc_jpy、ltc_btc、xrp_jpy、eth_btc、mona_jpy、mona_btc、bcc_jpy、bcc_btc
action: show、upsert、delete

  サンプル:

    CQの表示              全通貨ペア         candlestick s
    CQの表示     　       個別通貨ペア(曖昧検索)   candlestick s btc
    CQの登録/更新　       全通貨ペア         candlestick u
    CQの登録/更新　       個別通貨ペア       candlestick u btc_jpy
    CQの削除              全通貨ペア         candlestick d
    CQの削除              個別通貨ペア       candlestick d btc_jpy
    tickデータを登録　    ランダムの通貨ペア candlestick tick
    tickデータを登録      個別通貨ペア       candlestick tick btc_jpy
    depthデータを登録　    ランダムの通貨ペア candlestick depth
    depthデータを登録      個別通貨ペア       candlestick depth btc_jpy
  Kapacitor:
    Taskの表示　               candlestick task show
    Taskの登録/更新　          candlestick task upsert
    Taskの削除　               candlestick task delete

```

## 注意
「candlestick task upsert」を使う前に、下記のkapacitor設定が必要です。

kapacitor.conf

```
[[httppost]]
  endpoint = "candlestick"
  url = "https://publishのurl"
```

このバグの課題：https://bitbankcc.backlog.jp/view/BRONX-234
