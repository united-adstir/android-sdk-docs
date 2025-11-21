# WebViewアプリでのバナー広告の配信

adstirの広告タグを使用して、WebViewアプリで広告を配信することができます。  

## 広告ダグの取得

1. 管理画面にログインして、対象の枠の「タグ/SDK」を選択してください。
![tag01](../../init/Adstir_sdk_tutorial_01.png)

2. 「広告タグ」より広告タグを取得してください。

下記のような広告タグが取得いただけます。
```HTML
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  app_id: "MEDIA-XXXXXXXX",
  ad_spot: 1,
  center: false
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir.js"></script>
```

## originの追加
取得した広告タグにoriginパラメータを追加してください。  
originにはアプリのapplicationIdを設定してください。

```HTML
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  app_id: "MEDIA-XXXXXXXX",
  ad_spot: 1,
  center: false,
  origin: "com.foo.bar.baz" // applicationId
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir.js"></script>
```

## Android広告IDの追加

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

HTMLを生成する際に`{ここに広告識別子を書き出す}`の部分を、取得した広告識別子で置換してください。なお、広告識別子は、[Android広告IDの使用](https://play.google.com/about/monetization.html#ads-policy)に記載の通り、オプトアウトされている場合の利用が制限されております。下記コードのコメントに記載の通り、適切な対応をお願い致します。  

```HTML
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  app_id: "MEDIA-XXXXXXXX",
  ad_spot: 1,
  center: false,
  origin: "com.foo.bar.baz",
  // 以下の三行を適切に設定してください
  lmt: false, // ユーザーがオプトアウトしている場合は、trueを設定してください
  id: "google", // 広告識別子の種類(Google - GAID)
  uid: "{ここに広告識別子を書き出す}" // 広告識別子
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir.js"></script>
```

## OSバージョンの追加

アプリに掲載する広告は、OSバージョンを送信することでさらなる収益化が可能になる場合があります。

OSバージョンの取得方法は、下記取得サンプルまたは[公式ドキュメント](https://developer.android.com/reference/android/os/Build.VERSION#RELEASE)(英語)をご覧下さい。  

```java
String osVersion = android.os.Build.VERSION.RELEASE;
```

HTMLを生成する際に`{ここにOSバージョンを書き出す}`の部分を、取得したOSバージョンで置換してください。

```HTML
<script type="text/javascript">
var adstir_vars = {
  ver: "4.0",
  platform: "webview",
  app_id: "MEDIA-XXXXXXXX",
  ad_spot: 1,
  center: false,
  origin: "com.foo.bar.baz",
  lmt: false,
  id: "google",
  uid: "{ここに広告識別子を書き出す}",
  os_version: "{ここにOSバージョンを書き出す}" // 取得したOSバージョン
};
</script>
<script type="text/javascript" src="https://js.ad-stir.com/js/adstir.js"></script>
```