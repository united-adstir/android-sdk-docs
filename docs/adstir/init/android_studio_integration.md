# Android Studioによる組み込み

## build.gradleの編集
アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="5 9"
repositories {
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
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://adcolony.bintray.com/AdColony' } // adcolony
    maven { url 'https://github.com/glossom-dev/GlossomAds-Android/raw/master' } // adcorsa
    maven { url 'https://imobile-maio.github.io/maven' } // maio
    maven { url 'http://fan-adn.github.io/nendSDK-Android-lib/library' } // nend
    maven { url 'https://s3.amazonaws.com/moat-sdk-builds' } // mopub
    maven { url 'https://imobile.github.io/adnw-sdk-android' } // imobile
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter:${adstir_version}"
}
```