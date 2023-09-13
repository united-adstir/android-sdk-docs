# Android Studioによる組み込み

## build.gradleの編集
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="6 10"
repositories {
    google()
    maven { url 'https://cdnp.ad-stir.com/m2' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
}
```

### メディエーションアダプタの導入


#### 動画リワード・全画面インタースティシャル広告
動画リワード・全画面インタースティシャル広告をお使いの場合はメディエーションアダプタを導入してください。
下記の設定で、動画リワード・全画面インタースティシャル広告に対応したメディエーションアダプタが一括で導入されます。
ネットワークについては[こちら](../network/index.md)をご覧ください。


アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

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
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter:${adstir_version}"
}
```