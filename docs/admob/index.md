# AdMob広告について

## 前提条件

- Android Studio 3.2以上
- minSdkVersion 24以上
- compileSdkVersion 35以上
- AndroidX 必須

!!! Info
    [こちら](https://developer.android.com/jetpack/androidx/migrate?hl=ja#migrate)を参考にAndroidXへ移行してください。

## 事前準備

[AdMobのスタートガイド](https://developers.google.com/admob/android/next-gen/quick-start?hl=ja)を参考に、AdMobの設定をおこなってください。
AdMobアダプタはGoogle Mobile Ads SDK version {{ version.google }}でビルドし、Google Mobile Ads SDK version {{ version.google }} および、GMA Next-Gen SDK version {{ version.gma_next_gen }}にてテストを行なっております。

### メディエーションの準備

[AdMobメディエーション](https://developers.google.com/admob/android/next-gen/mediation?hl=ja)を行うために、アドネットワークのSDKとアダプターをプロジェクトへ導入します。

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


GMA Next Gen SDKを利用する場合は`play-services-ads`モジュールと`play-services-ads-lite`モジュールの両方をすべての依存関係から除外します。

```groovy hl_lines="1 4"
configurations.configureEach {
    exclude(group = "com.google.android.gms", module = "play-services-ads")
    exclude(group = "com.google.android.gms", module = "play-services-ads-lite")
}
```

## 広告の実装

AdMobの実装ガイドをご覧ください

* [バナー](https://developers.google.com/admob/android/next-gen/banner?hl=ja)
* [インタースティシャル](https://developers.google.com/admob/android/next-gen/interstitial?hl=ja)
* [ネイティブ](https://developers.google.com/admob/android/next-gen/native?hl=ja)
* [動画リワード](https://developers.google.com/admob/android/next-gen/rewarded?hl=ja)

### テストデバイスの追加
[開発時にはテスト端末を追加する](https://developers.google.com/admob/android/test-ads?hl=ja#add_your_test_device)より、広告リクエスト時にデバイスIDの設定をおこなってください。
こちらの設定をおこなった際には、アプリケーションのリリース前には該当コードの削除をお願いいたします。
