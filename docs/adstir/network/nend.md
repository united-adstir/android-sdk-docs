# nend広告の導入

## 対応OS

Android 4.4以上

## SDKの組み込み

### Android Studioによる組み込み(推奨)
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="7 20"
repositories {
    google()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://fan-adn.github.io/nendSDK-Android-lib/library' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-nend:${adstir_version}"
    // ご利用されているライブラリが競合した際は下記のバージョンをご利用されているライブラリのバージョンへ書き換えてください。
    // configurations.all {
    //     resolutionStrategy.force "org.jetbrains.kotlin:kotlin-stdlib-jdk7:x.x.x"
    //     resolutionStrategy.force "org.jetbrains.kotlinx:kotlinx-coroutines-android:x.x.x"
    //     resolutionStrategy.force "androidx.appcompat:appcompat:x.x.x"
    //     resolutionStrategy.force "androidx.constraintlayout:constraintlayout:x.x.x"
    //     resolutionStrategy.force "androidx.preference:preference:x.x.x"
    // }
}
```

### 手動組み込み
#### SDKの準備
nendのSDKは、VideoAdSDKBundledのパッケージに同梱されております。
作成された動画枠の`動画SDK (Android / AAR形式)`より取得いただけます。

#### SDKの組み込み
初期設定の[SDKの手動組み込み](../init/manual_integration.md)の完了後、下記の手順で追加してください。

1. File -> New -> New Module -> Import .JAR/.AAR Package より`nendSDK-x.x.x.aar`, `adstir-mediationadapter-adapter-nend.aar`を追加します。
2. File -> Project Structure -> Dependencies -> app より`nendSDK-x.x.x`, `adstir-mediationadapter-adapter-nend`を追加します。
3. アプリケーションレベルのbuild.gradleに依存関係を設定します。

```groovy hl_lines="1 7"
dependencies {
    implementation 'org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.4.32'
    implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.9'
    implementation 'androidx.appcompat:appcompat:1.2.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.0.4'
    implementation 'androidx.preference:preference:1.1.1'
}
```
