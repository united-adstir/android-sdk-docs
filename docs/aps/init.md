# Amazon Publisher Services(APS)の初期設定

APSの広告は下記のものに対応しております。

* AdMobバナー
* AdMobインタースティシャル

## プロジェクトへAPSの導入

APSのSDKとアダプター、アドネットワークのSDKとアダプターをプロジェクトへ導入します。

### Android Studioで導入する場合

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定することで、adstirが利用するアドネットワークのSDKとアダプターを一括で導入することができます。

```groovy hl_lines="12 16"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url "https://imobile-maio.github.io/maven" } // maio
    maven { url 'https://fan-adn.github.io/nendSDK-Android-lib/library' } // nend
    maven { url "https://imobile.github.io/adnw-sdk-android" } // imobile
    maven { url 'https://github.com/zucks/ZucksAdNetworkSDK-Maven/raw/master/' } // zucks
    maven { url 'https://artifact.bytedance.com/repository/pangle' } // TikTok
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:admob-package:${adstir_version}"
}
```

### 手動で導入する場合

営業担当にお問い合わせください。


## APSの初期化

営業担当がお知らせしたAPSのapp idを用いて、下記のように初期化を行います。

```java hl_lines="3 4 5 6 7 10 11"
import com.amazon.device.ads.AdRegistration;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        AdRegistration.getInstance("your_app_id", this);
    }
}
```

テスト時には下記を追加します。
アプリをリリースする前には下記のコードは削除してください。

```java
AdRegistration.enableTesting(true);
```

## 広告を実装する

* [バナー広告](banner.md)
* [インタースティシャル広告](interstitial.md)

## Google Play データ セーフティ セクションに記載する内容

2022年4月以降、Google Playで公開するアプリでユーザーデータをどの様に収集、処理するかを申告する必要がございます。
枠しくは「[Google Play のデータ セーフティ セクションの情報を提供する](https://support.google.com/googleplay/android-developer/answer/10787469?hl=ja)」ページをご覧ください。

APSの記載内容につきましては営業担当にお問い合わせください。
