# Zucks広告の導入

## 対応OS

Android 4.4以上

## SDKの組み込み

### Android Studioによる組み込み(推奨)
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="7 12"
repositories {
    google()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://github.com/zucks/ZucksAdNetworkSDK-Maven/raw/master/' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-zucks:${adstir_version}"
}
```

### 手動組み込み
#### SDKの準備
ZucksのSDKは、SwipeInterstitialSDKBundledのパッケージに同梱されております。
作成された動画枠の`スワイプインタースティシャルSDK (Android / AAR形式)`より取得いただけます。

#### SDKの組み込み
初期設定の[SDKの手動組み込み](../init/manual_integration.md)の完了後、下記の手順で追加してください。

1. File -> New -> New Module -> Import .JAR/.AAR Package より`zucks-ad-network-sdk-core-x.x.x.aar`, `adstir-mediationadapter-adapter-zucks.aar`を追加します。
2. File -> Project Structure -> Dependencies -> app より`zucks-ad-network-sdk-core-x.x.x.aar`, `adstir-mediationadapter-adapter-zucks`を追加します。
