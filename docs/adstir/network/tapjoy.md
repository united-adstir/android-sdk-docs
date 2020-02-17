# TapJoy広告の導入

## 対応OS

Android 4.4以上

## SDKの組み込み

### Android Studioによる組み込み(推奨)
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="5 10"
repositories {
    maven { url 'https://cdnp.ad-stir.com/m2' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "x.x.x" 
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-tapjoy:${adstir_version}"
}
```

### 手動組み込み
#### SDKの準備
TapJoyのSDKは、VideoAdSDKBundledのパッケージに同梱されております。  
作成された動画枠の`動画SDK (Android / AAR形式)`より取得いただけます。

#### SDKの組み込み
初期設定の[SDKの手動組み込み](../init/manual_integration.md)の完了後、下記の手順で追加してください。

1. File -> New -> New Module -> Import .JAR/.AAR Package より`tapjoyconnectlibrary.jar`, `androidwebviewmediation-adapter-tapjoy.aar`を追加します。
2. File -> Project Structure -> Dependencies -> app より`tapjoyconnectlibrary`, `androidwebviewmediation-adapter-tapjoy`を追加します。
