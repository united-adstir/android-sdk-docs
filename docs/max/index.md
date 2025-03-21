# AppLovin MAXメディエーションの設定

## 前提条件

* Android Studio 3.2以上
* minSdkVersion 23以上
* compileSdkVersion 34以上
* AndroidX 必須

## 事前準備

[AppLovin MAXのスタートガイド](https://dash.applovin.com/documentation/mediation/android/getting-started/integration)を参考に、AppLovin MAXの導入を行なってください。  
AppLovin MAXアダプタは[Applovin SDK version {{version.applovin}}](https://github.com/AppLovin/AppLovin-MAX-SDK-Android/releases)でビルドおよびテストを行なっています。

## カスタムSDKネットワーク導入

[カスタムSDKネットワーク導入](https://dash.applovin.com/documentation/mediation/android/mediation-setup/custom-sdk)を行うために、adstirのSDKとメディエーションアダプターを追加します。  

### SDKの導入

アプリケーションレベルのbuild.gradleにmavenリポジトリと依存関係を設定することで、SDKとアダプターを一括で導入することができます。

```groovy hl_lines="7 11"
repositories {
    google()
    mavenCentral()
    maven { url 'https://cdnp.ad-stir.com/m2' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:applovin-max-mediation-adapter:${adstir_version}"
}
```

そのほか、AppLovin MAXメディエーションで利用していないネットワークを追加することをおすすめします。
導入する場合は[こちら](../adstir/network/index.md)を参考に導入していただくか、営業担当までご連絡ください。


## カスタムSDKネットワークを追加する

[カスタムSDKネットワークを追加](https://dash.applovin.com/documentation/mediation/android/mediation-setup/custom-sdk#step-1.-add-custom-sdk-network-settings)します。その際、カスタムネットワークに関する情報は下記の値を入力してください。

| 項目 | 入力内容 |
| :--- | :--- |
| Network Type | SDK |
| Custom Network Name | adstir |
| Android Adapter Class Name | com.ad_stir.mediation.applovin.AdstirMediationAdapter |

## カスタムSDKネットワークを有効にする

[カスタムSDKネットワークを有効](https://dash.applovin.com/documentation/mediation/android/mediation-setup/custom-sdk#step-2.-enable-the-custom-sdk-network)にします。
各広告種別に対する設定は下記の設定をお願いします。

### バナー

| 項目 | 入力内容 |
| :--- | :--- |
| App ID | adstirメディアID |
| Placement ID | adstir枠No |
| Custom Parameters | `{"is_filler":true}` |

* パスバック(MAXへの案件切れ通知)が必要な場合はfalseを、不要な場合はtrueを設定してください。
* パスバックを行う場合は一部の広告が配信できません

### ネイティブ

| 項目 | 入力内容 |
| :--- | :--- |
| App ID | adstirメディアID |
| Placement ID | adstir枠No |
| Custom Parameters | 設定不要 |

### リワード

| 項目 | 入力内容 |
| :--- | :--- |
| App ID | adstirメディアID |
| Placement ID | adstir枠No |
| Custom Parameters | `{"spotNos":"カンマ区切りのアプリで利用する動画リワード/全画面インタースティシャル広告の全枠No"}` |

* Custom Parametersの設定例 : `{"spotNos":"2,3"}`

### インタースティシャル

| 項目 | 入力内容 |
| :--- | :--- |
| App ID | adstirメディアID |
| Placement ID | adstir枠No |
| Custom Parameters | `{"spotNos":"カンマ区切りのアプリで利用する動画リワード/全画面インタースティシャル広告の全枠No"}` |

* Custom Parametersの設定例 : `{"spotNos":"2,3"}`
