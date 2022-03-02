# 変更履歴

## v2.15.23 (2021/12/20)

- adstir SDKのcompileSdkVersion/targetSdkVersionを31に変更
- Android 12対応
    - adstir SDKに`com.google.android.gms.permission.AD_ID`の権限を追加しました
        - ターゲットAPIレベル31以上を対象とするアプリで広告IDを取得するために`AD_ID`の権限が必要になるアップデートが2022年に予定されております
        - 詳細については[こちら](https://support.google.com/googleplay/android-developer/answer/6048248?hl=ja&ref_topic=2364761)をご覧ください
- SDKの安定性向上
- bundle SDKの更新
    - [AdColony 4.6.5](https://github.com/AdColony/AdColony-Android-SDK/releases/tag/4.6.5)
        - Android 12の対応が含まれております
    - [AppLovin 10.3.5](https://github.com/AppLovin/AppLovin-MAX-SDK-Android/releases/tag/release_10_3_5)
    - [Maio 1.1.16](https://github.com/imobile-maio/maio-Android-SDK/releases/tag/v1.1.16)
        - Google Play Console上でエラーが発生する場合がある問題が解消されております
    - [Nend 8.0.1](https://github.com/fan-ADN/nendSDK-Android-pub/releases/tag/8.0.1)
    - TikTok 4.1.1.2

## v2.15.22 (2021/10/11)

- 動画広告プレイヤーの安定性向上
- MoPubのサポートOSバージョンを5.0以上に変更
- AdCorsa SDKのバンドル終了
- [facebookのウォータフォールでの配信終了](https://www.facebook.com/business/help/178983086270324?id=211412110064838)に伴い、AdMobパッケージのfacebookのバンドル終了
- bundle SDKの更新
    * [AdColony 4.6.2](https://github.com/AdColony/AdColony-Android-SDK/releases/tag/4.6.2)
    * [AppLovin 10.3.3](https://github.com/AppLovin/AppLovin-MAX-SDK-Android/releases/tag/release_10_3_3)
    * [Maio 1.1.15](https://github.com/imobile-maio/maio-Android-SDK/releases/tag/v1.1.15)
    * [MoPub 5.18.0](https://github.com/mopub/mopub-android-sdk/releases/tag/v5.18.0)
        * MavenリポジトリがMaven Centralに変更されました
    * [Nend 8.0.0](https://github.com/fan-ADN/nendSDK-Android-pub/releases/tag/8.0.0)
        * Android 12の対応が含まれております
        * AdMobパッケージにはNendのAdMob用アダプターは含まれておりません
    * [TapJoy 12.8.1](https://dev.tapjoy.com/jp/android-sdk/Changelog#id-1281-2021-05-25)
        * MavenリポジトリがTapJoyのリポジトリに変更されました
    * TikTok 3.9.0.5
        * MavenリポジトリがTikTokのリポジトリに変更されました
    * [UnityAds 3.7.5](https://github.com/Unity-Technologies/unity-ads-android/releases/tag/3.7.5)
        * MavenリポジトリがMaven Centralに変更されました
    * [Zucks 4.8.6](https://ms.zucksadnetwork.com/media/sdk/manual/android)
        * MavenリポジトリがZucksのリポジトリに変更されました

## v2.15.21 (2021/09/15)

- AdMobメディエーションのアダプタ改修 (バナー)
    - 一部のアプリで配信できない問題に対応しました

## v2.15.20 (2021/08/27)

- AdMobメディエーションのアダプタ改修 (バナー)

## v2.15.19 (2021/08/10)

- Google Mobile Ads SDK v20 への対応
    - v20 SDKではAPIが変更されています
    - AdMobをご利用でv20 SDKへ移行する場合は[こちら](https://developers.google.com/admob/android/migration)を参考にしてください
    - APIの変更に伴い[リワード広告の従来のAPI](https://developers.google.com/admob/android/rewarded-video)のサポートを終了しました

## v2.15.18 (2021/06/07)

- 5Gネットワークへの対応

## v2.15.17 (2021/03/10)

- bundle SDKの更新
    * [AdColony 4.4.1](https://github.com/AdColony/AdColony-Android-SDK/releases/tag/4.4.1)
        * MavenリポジトリがMaven Centralに変更されました
    * [AppLovin 9.14.12](https://github.com/AppLovin/AppLovin-MAX-SDK-Android/releases/tag/release_9_14_12)
        * MavenリポジトリがMaven Centralに変更されました
## v2.15.16 (2020/12/15)

- MoPub用アダプターの安定性向上

## v2.15.15 (2020/12/09)

- Nendアダプターの修正
    - 依存関係に`androidx.preference:preference`が追加
- AdMobパッケージにNendのAdMob用アダプターを追加

## v2.15.14 (2020/11/26)

- bundle SDKの更新
    * [MoPub 5.15.0](https://github.com/mopub/mopub-android-sdk/releases/tag/v5.15.0)
    * AdMobパッケージにmaioのAdMob用アダプターを追加

## v2.15.13 (2020/10/21)

- adstir SDKのcompileSdkVersion/targetSdkVersionを30に変更
- bundle SDKの更新
    * [Nend 7.0.0](https://github.com/fan-ADN/nendSDK-Android-pub/releases/tag/7.0.0)
        * Android 11 (API level 30)対応版SDKです
        * 7.0.0未満のnendSDKをtargetSdkVersion 30でビルドした場合、動画広告やインタラクティブ広告が正常に動作しません
    * [maio 1.1.13](https://github.com/imobile-maio/maio-Android-SDK/releases/tag/v1.1.13)
        * Android 11 (API level 30)対応版SDKです
        * AdMobパッケージにはmaioのAdMob用アダプターは含まれておりません
    * [UnityAds 3.4.8](https://github.com/Unity-Technologies/unity-ads-android/releases/tag/3.4.8)
        * Android 11 (API level 30)対応版SDKです
        * Android 11 (API level 30)でのクラッシュが修正されました

## v2.15.12 (2020/10/09)

- Mobvista(Mintegral) SDKのBundleを終了


## v2.15.11 (2020/10/08)

- bundle SDKの更新
    * [MoPub 5.14.0](https://github.com/mopub/mopub-android-sdk/releases/tag/v5.14.0)
        * Android 11 (API level 30)対応版SDKです

## v2.15.10 (2020/09/04)

- bundle SDKの更新
    * maio 1.1.12
        * AdMobパッケージにはmaioのAdMob用アダプターは含まれておりません

## v2.15.9 (2020/08/21)

- TikTok SDK (3.1.5.1) との動画リワード/全画面インタースティシャル 接続

## v2.15.8 (2020/08/11)

- bundle SDKの更新
    * Mobvista 14.0.1

## v2.15.7 (2020/08/06)

- Android OSの最小サポートバージョンを4.4(APIレベル19)に変更
- バナー広告の安定性向上
- bundle SDKの更新
    - MoPub 5.13.1

## v2.15.6 (2020/07/30)

- bundle SDKの更新
    * AdColony 4.1.4
    * AppLovin 9.13.1
    * Mobvista 14.2.5
    * TapJoy 12.6.1

## v2.15.5 (2020/07/16)

- 動画リワード、全画面インタースティシャル広告の安定性向上
- bundle SDKの更新
    - UnityAds 3.4.6
    - imobile 2.0.22


## v2.15.4 (2020/05/13)

- AdMobのアダプティブバナーに対応

## v2.15.3 (2020/04/06)

- Google Mobile Ads用の動画リワード用アダプターの安定性向上

## v2.15.2 (2020/02/12)

- bundle SDKの更新
    - Tapjoy 12.4.2

## v2.15.1 (2020/02/03)

- bundle SDKの更新
    - Tapjoy 12.4.1

## v2.15.0 (2020/01/23)

- bundle SDKの更新
    - AppLovin 9.10.5
    - Mobvista 10.1.71

- AdMobメディエーションアダプタの改修
    - [動画リワード新API](https://developers.google.com/admob/android/rewarded-ads?hl=ja)へ対応
    - adstir SDK本体とAdMobメディエーションアダプタを別々のSDKに分離

!!! Warning "Google AdManager/AdMobをご利用でv2.15.0以前のadstir SDKからアップデートされる皆様へ"
    Google Mobile Ads SDKの変更に伴い、adstir SDK本体(adstir-android-webviewsdk)に同梱していたAdMobメディエーションアダプタを分離しました。
    Google AdManager/AdMobをご利用でv2.15.0以前のadstir SDKからアップデートされる場合は[こちら](adstir/info/question.md#google-admanageradmobでadstirの広告が表示されません)をご覧ください。