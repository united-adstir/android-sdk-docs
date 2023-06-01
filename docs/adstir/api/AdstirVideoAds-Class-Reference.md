# AdstirVideoAds Class Reference
動画リワード広告と全画面インタースティシャル広告の初期化を行うクラスです。

## Instance Methods

### init

動画リワード広告、全画面インタースティシャル広告の初期化を行います。  
[動画リワード広告のコンストラクタ](reward/AdstirVideoReward-Class-Reference.md#adstirvideoreward)および、[全画面インタースティシャル広告のコンストラクタ](interstitial/AdstirInterstitial-Class-Reference.md#adstirinterstitial)より前に呼び出してください。

```java
public static void init(Activity activity, String mediaId, int[] spotNoArray)
```

* Parameters

|パラメータ||
|---|---|
|activity|アクティビティ|
|mediaId|メディアID|
|spotNoArray|動画リワード広告と全画面インタースティシャル広告の枠Noの配列|
