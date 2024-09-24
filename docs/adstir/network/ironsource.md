# ironSource広告の導入

## 対応OS

Android 5.0以上

## SDKの組み込み

### Android Studioによる組み込み(推奨)
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="7 12"
repositories {
    google()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://android-sdk.is.com/' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-ironsource:${adstir_version}"
}
```

### 手動組み込み

#### SDKの準備

ironSourceのSDKは、VideoAdSDKBundledのパッケージに同梱されております。
作成された動画枠の`動画SDK (Android / AAR形式)`より取得いただけます。
バナー広告をご利用される場合は営業担当にお問い合わせいただくか、Android Studioによる組み込みをご利用ください。

#### SDKの組み込み

初期設定の[SDKの手動組み込み](../init/manual_integration.md)の完了後、下記の手順で追加してください。

1. File -> New -> New Module -> Import .JAR/.AAR Package より`mediationsdk-x.x.x.aar`, `adstir-mediationadapter-adapter-ironsource.aar`を追加します。
2. File -> Project Structure -> Dependencies -> app より`mediationsdk-x.x.x`, `adstir-mediationadapter-adapter-ironsource`を追加します。