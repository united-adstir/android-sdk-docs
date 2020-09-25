# ネイティブライクバナー

ネイティブライクバナー広告は、ネイティブ広告をバナーのように配置して掲載する広告形式です。

## 一般的な掲載方法

アプリ内でテンプレートに合ったサイズのWebViewを作成していただき、そこに管理画面で取得できるタグを記述したHTMLファイルを表示するのみです。なお、綺麗なサイズで表示するためには、marginやpaddingを初期化する必要があります。

```HTML
<style type="text/css">
html,body { margin:0; padding:0 } /* marginとpaddingを0に */
</style>
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  type: "native",
  app_id: "MEDIA-XXXXX",
  ad_spot: 1,
  async: false,
  origin: "com.foo.bar.baz",
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir_native.js"></script>
```

## バナーサイズのリサイズ

ネイティブライクバナーは、自由にリサイズをすることが可能です。下記の様に、幅とスケールを指定することで、基本サイズ(テンプレート選択画面に記載)からリサイズできます。

```HTML
<style type="text/css">
html,body { margin:0; padding:0 } /* marginとpaddingを0に */
#adstir_native_widget_wrapper {
    width: 150px;
    height: 100px;
}
#adstir_native_widget {
    transform: scale(0.5);
    -webkit-transform: scale(0.5); /* 古いバージョンのOSに対応させる場合に必須 */
}
</style>
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  type: "native",
  app_id: "MEDIA-XXXXX",
  ad_spot: 1,
  async: false,
  origin: "com.foo.bar.baz",
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir_native.js"></script>
```

## Android広告IDの使用

アプリに掲載する広告は、広告識別子を送信することでさらなる収益化が可能になる場合があります。

広告識別子の取得方法は、下記取得サンプルと、[公式ドキュメント](https://developers.google.com/android/reference/com/google/android/gms/ads/identifier/package-summary#classes)(英語)をご覧下さい。  

```java
new AsyncTask<Void, Void, String>(){
    @Override
    protected String doInBackground(Void... params) {
        try {
            AdvertisingIdClient.Info info = AdvertisingIdClient.getAdvertisingIdInfo(context);
            if (info.isLimitAdTrackingEnabled()) {
                return null;
            } else {
                return info.getId();
            }
        } catch (GooglePlayServicesNotAvailableException | 
                 GooglePlayServicesRepairableException |
                 IOException | 
                 IllegalStateException e) {
            return null;
        }
    }
    @Override
    protected void onPostExecute(String advertisingId) {
        // 取得後の処理
    }
}.execute();
```

HTMLを生成する際に`{{ここに広告識別子を書き出す}}`の部分を、取得した広告識別子で置換してください。なお、広告識別子は、[Android広告IDの使用](https://play.google.com/about/monetization.html#ads-policy)に記載の通り、オプトアウトされている場合の利用が制限されております。下記コードのコメントに記載の通り、適切な対応をお願い致します。  

```HTML
<style type="text/css">
html,body { margin:0; padding:0 } /* marginとpaddingを0に */
</style>
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  type: "native",
  app_id: "MEDIA-XXXXX",
  ad_spot: 1,
  origin: "com.foo.bar.baz",
  // 以下の三行を適切に設定してください
  lmt: false, // ユーザーがオプトアウトしている場合は、trueを設定してください
  id: "google", // 広告識別子の種類(Google - GAID)
  uid: "{{ここに広告識別子を書き出す}}", // 広告識別子
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir_native.js"></script>
```

## よくある質問

### User−Agentの変更について

User-Agentを標準のものから変更された場合、正常に広告は配信されません。

独自のUser-Agentをご利用になられる場合には、既存のUser-Agentの末尾に、文字列を追加して頂くようにお願い致します。

例：
Mozilla/5.0 (iPhone; CPU iPhone OS 10_0_1 like Mac OS X) AppleWebKit/602.1.50 (KHTML, like Gecko) Mobile/14A403 **AdStir-IOS com.ad-stir.appli/2.7.2** <- 太字部分を追加

