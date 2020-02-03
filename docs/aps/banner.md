# Amazon Publisher Services(APS)のバナー広告の導入

!!! Warning "はじめに"
    APS SDKの初期化が必要です。[APSの設定](init.md)をご覧になり、SDKの初期化を先におこなってください。

## APSバナーへのリクエストを行う

### App Keyの登録

```java
AdRegistration.getInstance("YOUR_APP_KEY", getApplicationContext());
```

### `DTBAdSize`のインスタンスを生成します

広告サイズは実際に表示するバナー広告のサイズを、`YOUR_SLOT_UUID`には営業担当がお知らせしたIDを入力してください。
    
```java
DTBAdSize adSize = new DTBAdSize(320, 50, "YOUR_SLOT_UUID");
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
        AdView adView = (AdView) findViewById(R.id.aps_ad_view);

        AdRequest request = new AdRequest.Builder().build();
        adView.loadAd(request);
    }

    // APS bid returned
    @Override
    public void onSuccess(DTBAdResponse dtbAdResponse) {
        AdView adView = (AdView) findViewById(R.id.aps_ad_view);

        Bundle bundle = dtbAdResponse.getRenderingBundle();

        @SuppressWarnings("unchecked")
        AdRequest request = new AdRequest.Builder().addCustomEventExtrasBundle(APSAdMobCustomBannerEvent.class, bundle).build();
        adView.loadAd(request);
    }
});
```

## 実装例

```java
import com.amazon.admob_adapter.APSAdMobCustomBannerEvent;
import com.amazon.device.ads.AdError;
import com.amazon.device.ads.AdRegistration;
import com.amazon.device.ads.DTBAdCallback;
import com.amazon.device.ads.DTBAdRequest;
import com.amazon.device.ads.DTBAdResponse;
import com.amazon.device.ads.DTBAdSize;
import com.google.android.gms.ads.AdRequest;
import com.google.android.gms.ads.AdView;

public class MainActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        AdRegistration.getInstance("YOUR_APP_KEY", getApplicationContext());

        DTBAdSize adSize = new DTBAdSize(320, 50, "YOUR_SLOT_UUID");

        final DTBAdRequest adLoader = new DTBAdRequest();
        adLoader.setSizes(adSize);

        loader.loadAd(new DTBAdCallback() {

            // No APS bid returned
            @Override
            public void onFailure(AdError adError) {
                AdView adView = (AdView) findViewById(R.id.aps_ad_view);

                AdRequest request = new AdRequest.Builder().build();
                adView.loadAd(request);
            }

            // APS bid returned
            @Override
            public void onSuccess(DTBAdResponse dtbAdResponse) {
                AdView adView = (AdView) findViewById(R.id.aps_ad_view);

                Bundle bundle = dtbAdResponse.getRenderingBundle();

                @SuppressWarnings("unchecked")
                AdRequest request = new AdRequest.Builder().addCustomEventExtrasBundle(APSAdMobCustomBannerEvent.class, bundle).build();
                adView.loadAd(request);
            }
        });
    }
}

```
