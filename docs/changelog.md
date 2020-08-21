# 変更履歴

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
    Google AdManager/AdMobをご利用でv2.15.0以前のadstir SDKからアップデートされる場合は[こちら](adstir/question.md#google-admanageradmobでadstirの広告が表示されません)をご覧ください。