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

ご利用する広告種別毎にメディエーションアダプタを導入してください。
ネットワークについては[こちら](../network/index.md)をご覧ください。

下記が広告種別毎に全てのネットワークのメディエーションアダプターを導入例となります。

#### バナー広告

下記の設定で、バナー広告に対応したメディエーションアダプタが一括で導入されます。

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="8 12"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://android-sdk.is.com/'} // ironSource
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-ironsource:${adstir_version}"
}
```


#### 動画リワード・全画面インタースティシャル広告

下記の設定で、動画リワード・全画面インタースティシャル広告に対応したメディエーションアダプタが一括で導入されます。

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="11 15"
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
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter:${adstir_version}"
}
```

#### スワイプインタースティシャル広告

下記の設定で、動画リワード・全画面インタースティシャル広告に対応したメディエーションアダプタが一括で導入されます。

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定します。

```groovy hl_lines="8 12"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
    maven { url 'https://github.com/zucks/ZucksAdNetworkSDK-Maven/raw/master/' } // Zucks
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:adstir-mediationadapter-zucks:${adstir_version}"
}
```