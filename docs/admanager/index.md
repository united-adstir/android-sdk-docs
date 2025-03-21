# AdManager広告について

## 前提条件

- Android Studio 3.2以上
- minSdkVersion 23以上
- compileSdkVersion 34以上
- AndroidX 必須

## 事前準備

[AdManagerのスタートガイド](https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start)を参考に、AdManagerの設定をおこなってください。
Google Mobile Ads SDKは20.0.0以上をお使いください。

[Ad Manager app ID](https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start#configure_your_app)は弊社で登録後、営業担当よりお伝えします。

### メディエーションの準備

[メディエーション](https://developers.google.com/ad-manager/mobile-ads-sdk/android/mediate)を行うために、adstir SDKとアダプターをプロジェクトへ導入します。

#### Android Studioで導入する場合

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定することで、adstirが利用するアドネットワークのSDKとアダプターを一括で導入することができます。

```groovy hl_lines="11 23"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://imobile-maio.github.io/maven' } // maio
    maven { url 'https://imobile.github.io/adnw-sdk-android'} // imobile
    maven { url 'https://android-sdk.is.com/'} // ironSource
    maven { url 'https://artifact.bytedance.com/repository/pangle' } // TikTok
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-admob-mediation-adapter:${adstir_version}"

    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-applovin:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-imobile:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-ironsource:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-maio:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-unityads:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-tiktok:${adstir_version}")
}
```

#### 手動で導入する場合

1. [こちら](../adstir/init/manual_integration.md#sdkの手動組み込み)を参考にadstirの動画パッケージを組み込みます
    * バナー広告のみをご利用される場合は営業担当までお問い合わせください
1. [AdManagerのスタートガイド](https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start#import_the_mobile_ads_sdk)を参考にGoogleMobileAds SDKを入れます
1. ダウンロードした各SDKをプロジェクトへ追加します

## 広告の実装

AdManagerの実装ガイドをご覧ください。
ad_unit_idは営業担当よりお伝えしますが、もともとのad_unit_idが

```
/1234/banner_id
```

の場合、先頭にadstirのネットワークコード(34264398)とカンマを追加し、

```
/34264398,1234/banner_id
```
となります。

* [バナー](https://developers.google.com/ad-manager/mobile-ads-sdk/android/banner)
* [アダプティブバナー](https://developers.google.com/ad-manager/mobile-ads-sdk/android/banner/adaptive)
* [インタースティシャル](https://developers.google.com/ad-manager/mobile-ads-sdk/android/interstitial)
* [ネイティブ](https://developers.google.com/ad-manager/mobile-ads-sdk/android/native/start)
* [動画リワード](https://developers.google.com/ad-manager/mobile-ads-sdk/android/rewarded)

    !!! warning
        アダプティブバナーを実装する場合は、最新バージョンのGoogle Mobile Ads SDK をご利用ください。

### テストデバイスの追加
[開発時にはテスト端末を追加する](https://developers.google.com/ad-manager/mobile-ads-sdk/android/test-ads#add_your_test_device_programmatically)より、広告リクエスト時にデバイスIDの設定をおこなってください。
こちらの設定をおこなった際には、アプリケーションのリリース前には該当コードの削除をお願いいたします。
