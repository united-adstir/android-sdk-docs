# 変更履歴

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