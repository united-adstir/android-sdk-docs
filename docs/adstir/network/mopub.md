# MoPub広告の導入

## 対応OS

Android 4.4以上

## SDKの組み込み

### Android Studioによる組み込み(推奨)
アプリケーションレベルのbuild.gradleにコンパイルオプションとmavenリポジトリと依存関係を設定します。

```groovy hl_lines="1 6 12 24"
android {
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}

repositories {
    maven { url 'https://cdnp.ad-stir.com/m2' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-mopub:${adstir_version}"
    // ご利用されているライブラリが競合した際は下記のバージョンをご利用されているライブラリのバージョンへ書き換えてください。
    // configurations.all {
    //     resolutionStrategy.force "androidx.legacy:legacy-support-v4:x.x.x"
    //     resolutionStrategy.force "androidx.annotation:annotation:x.x.x"
    //     resolutionStrategy.force "androidx.recyclerview:recyclerview:x.x.x"
    //     resolutionStrategy.force "androidx.appcompat:appcompat:x.x.x"
    // }
}
```

### 手動組み込み
#### SDKの準備
MoPubのSDKは、VideoAdSDKBundledのパッケージもしくはSwipeInterstitialSDKBundledのパッケージに同梱されております。
作成された動画枠の動画SDK (Android)もしくはスワイプインタースティシャル広告枠のスワイプインタースティシャルSDK (Android)より取得いただけます。

#### SDKの組み込み
初期設定の[SDKの手動組み込み](../init/manual_integration.md)の完了後、下記の手順で追加してください。

1. File -> New -> New Module -> Import .JAR/.AAR Package より以下のファイルを追加します。
    * `mopub-sdk-banner-x.x.x.aar`
    * `mopub-sdk-base-x.x.x.aar`
    * `mopub-sdk-fullscreen-x.x.x.aar`
    * `mopub-sdk-native-static-x.x.x.aar`
    * `adstir-mediationadapter-adapter-mopub.aar`

1. File -> Project Structure -> app -> Dependencies より以下を追加します。
    * `mopub-sdk-banner-x.x.x`
    * `mopub-sdk-base-x.x.x`
    * `mopub-sdk-fullscreen-x.x.x`
    * `mopub-sdk-native-static-x.x.x`
    * `adstir-mediationadapter-adapter-mopub`

3. アプリケーションレベルのbuild.gradleに依存関係を設定します。

```groovy hl_lines="1 8"
dependencies {
    implementation "com.mopub.volley:mopub-volley:2.1.0"
    implementation "com.google.android.exoplayer:exoplayer:2.9.5"
    implementation "androidx.legacy:legacy-support-v4:1.0.0"
    implementation "androidx.annotation:annotation:1.1.0"
    implementation "androidx.recyclerview:recyclerview:1.1.0"
    implementation "androidx.appcompat:appcompat:1.1.0"
    implementation "com.mopub:omsdk-android:1.3.4"
}
```
