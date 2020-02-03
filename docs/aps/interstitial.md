# Amazon Publisher Services(APS)のバナー広告の導入

!!! Warning "はじめに"
    APS SDKの初期化が必要です。[APSの設定](init.md)をご覧になり、SDKの初期化を先におこなってください。

## APSインタースティシャルへのリクエストを行う

### App Keyの登録

```java
AdRegistration.getInstance("YOUR_APP_KEY", getApplicationContext());
```

### `DTBAdSize`のインスタンスを生成します

広告サイズは実際に表示するバナー広告のサイズを、`YOUR_SLOT_UUID`には営業担当がお知らせしたIDを入力してください。
    
```java
DTBAdSize adSize = new DTBAdSize.DTBInterstitialAdSize("YOUR_SLOT_UUID");
```

### `DTBAdLoader`のインスタンスを生成し、`DTBAdSize`を設定する

```java
final DTBAdRequest adLoader = new DTBAdRequest();
adLoader.setSizes(adSize);
```

### APSの入札リクエストとコールバックの設定
loadAdを呼び出して入札リクエストを行います。

APSが入札した場合はonSuccessが、入札しなかった場合はonFailureが呼ばれます。
APSの入札結果を元に、AdMobへ広告リクエストを行います。

onSuccessが呼ばれた場合は、AdMobへCustomEventExtrasBundleを付与して広告リクエストを行い、
onFailureが呼ばれた場合は、AdMobへ追加情報を付与せずにリクエストを行います。
AdMobの実装については[こちら](/admob#広告の実装)をご覧ください。

```java
loader.loadAd(new DTBAdCallback() {

    // No APS bid returned
    @Override
    public void onFailure(AdError adError) {
        AdRequest adRequest = new AdRequest.Builder().build();
        mInterstitialAd.loadAd(adRequest);
        APSAdMobCustomInterstitialEvent.setAdMobInterstitial(mInterstitialAd);
    }

    // APS bid returned
    @Override
    public void onSuccess(DTBAdResponse dtbAdResponse) {
        Bundle bundle = dtbAdResponse.getRenderingBundle();

        AdRequest adRequest = new AdRequest.Builder().addCustomEventExtrasBundle(APSAdMobCustomInterstitialEvent.class, bundle).build();

        mInterstitialAd.loadAd(adRequest);
        APSAdMobCustomInterstitialEvent.setAdMobInterstitial(mInterstitialAd);
    }
});
```


### 広告を表示する

広告の準備ができているか確認してから広告を表示します。

```java
if (mInterstitialAd.isLoaded()){
    mInterstitialAd.show();
}
```
