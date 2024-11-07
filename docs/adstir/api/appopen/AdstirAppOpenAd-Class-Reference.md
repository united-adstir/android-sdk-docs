# AdstirAppOpenAd Class Reference
アプリ起動時広告を呼び出すクラスです。

## Constructor
### AdstirAppOpenAd
管理画面から取得したメディアIDと枠Noを設定してください。

```java
public AdstirAppOpenAd(Activity activity, String mediaId, int spotNo) 
```

* Parameters

|パラメータ||
|---|---|
|activity|アクティビティ|
|mediaId|メディアID|
|spotNo|枠No|

## Instance Methods

### setAdstirAppOpenAdListener

リスナーを設定します。広告の読み込み完了時や広告が閉じられた時などに実行する処理を指定することが出来ます。  
AdstirAppOpenAdListenerの詳細については[こちら](AdstirAppOpenAdListener-Interface-Reference.md)をご覧ください。

```java
public void setAdstirAppOpenAdListener(AdstirAppOpenAdListener listener)
```

* Parameters

|パラメータ||
|---|---|
|listener|リスナー|

### load

広告の読み込みを行います。

```java
public void load()
```

### canShow
広告の表示可否を判定します。

```java
public boolean canShow()
```

### show

広告の表示を行います。

```java
public void show()
```

### destroy

インスタンスを破棄します。

```java
public void destroy()
```