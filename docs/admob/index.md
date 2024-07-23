# AdMob広告について

## 前提条件

- Android Studio 3.2以上
- minSdkVersion 21以上
- compileSdkVersion 34以上
- AndroidX 必須

!!! Info
    [こちら](https://developer.android.com/jetpack/androidx/migrate?hl=ja#migrate)を参考にAndroidXへ移行してください。

## 事前準備

[AdMobのスタートガイド](https://developers.google.com/admob/android/quick-start?hl=ja)を参考に、AdMobの設定をおこなってください。
AdMobアダプタはGoogle Mobile Ads SDK version {{ version.google }}でビルドおよびテストを行なっています。

### メディエーションの準備

[AdMobメディエーション](https://developers.google.com/admob/android/mediate?hl=ja)を行うために、アドネットワークのSDKとアダプターをプロジェクトへ導入します。

#### Android Studioで導入する場合

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定することで、adstirが利用するアドネットワークのSDKとアダプターを一括で導入することができます。

```groovy hl_lines="10 21"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url "https://imobile-maio.github.io/maven" } // maio
    maven { url "https://imobile.github.io/adnw-sdk-android" } // imobile
    maven { url 'https://artifact.bytedance.com/repository/pangle' } // TikTok
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-admob-mediation-adapter:${adstir_version}"

    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-applovin:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-imobile:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-maio:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-unityads:${adstir_version}")
    implementation("com.ad-stir.mediationadapter:adstir-mediationadapter-tiktok:${adstir_version}")
}
```

#### 手動で導入する場合

1. [こちら](../adstir/init/manual_integration.md#sdkの手動組み込み)を参考にadstirの動画パッケージを組み込む
1. [AdMobのスタートガイド](https://developers.google.com/admob/android/quick-start?hl=ja#manual_download)を参考にGoogleMobileAds SDKを入れる

## 広告の実装

AdMobの実装ガイドをご覧ください

* [バナー](https://developers.google.com/admob/android/banner?hl=ja)
* [インタースティシャル](https://developers.google.com/admob/android/interstitial?hl=ja)
* [ネイティブ](https://developers.google.com/admob/android/native/start?hl=ja)
* [動画リワード](https://developers.google.com/admob/android/rewarded-ads?hl=ja)
* [アダプティブバナー](https://developers.google.com/admob/android/banner/adaptive?hl=ja)

    !!! warning
        アダプティブバナーを実装する場合は、最新バージョンのGoogle Mobile Ads SDK をご利用ください。

### テストデバイスの追加
[開発時にはテスト端末を追加する](https://developers.google.com/admob/android/test-ads?hl=ja#add_your_test_device)より、広告リクエスト時にデバイスIDの設定をおこなってください。
こちらの設定をおこなった際には、アプリケーションのリリース前には該当コードの削除をお願いいたします。
