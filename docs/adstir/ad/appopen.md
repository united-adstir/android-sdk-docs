# アプリ起動時広告の導入

アプリ起動時広告はユーザーがアプリを開いたときまたはアプリに戻ったときに表示する広告です。  
アプリの読み込み画面(スプラッシュ画面)がある場合は、その画面の表示後にアプリ起動時広告を表示してください。  
アプリ起動時広告を導入する際は、広告の表示頻度を調整しアプリのユーザビリティが低下しないようにご注意ください。  
子供を対象とするアプリではアプリ起動時広告は使用しないでください。


## 対応OS

Android 5.0以上

## 広告の設定

### 1.アプリ起動時広告のインスタンスを生成

`AdstirAppOpenAd`のインスタンスを生成します。
```java
AdstirAppOpenAd adstirAppOpenAd = new AdstirAppOpenAd(this, "メディアID", 枠No);
```

### 2.リスナーの生成

アプリ起動時広告のイベント通知を行うリスナーのインスタンスを生成します。

```java
// リスナーの定義
private AdstirAppOpenAdListener listener = new AdstirAppOpenAdListener() {
    @Override
    public void onLoad(int spot_no) {
      // 広告の読み込みが完了した時の処理を記述できます。
    }
    @Override
    public void onFailed(int spot_no) {
      // 広告の読み込みが失敗した時の処理を記述できます。
    }
    @Override
    public void onStart(int spot_no) {
      // 広告が表示された時の処理を記述できます。
    }
    @Override
    public void onStartFailed(int spot_no) {
      // 広告の表示に失敗した時の処理を記述できます。
    }
    @Override
    public void onClose(int spot_no) {
      // 広告が閉じられた時の処理を記述できます。
    }
  };

// 上で定義したリスナーを登録します。
adstirAppOpenAd.setAdstirAppOpenAdListener(listener);
```

### 3.アプリ起動時広告の読み込み

アプリ起動時広告の読み込みを行います。

```java
adstirAppOpenAd.load();
```

### 4.アプリ起動時広告の表示

読み込みが完了したアプリ起動時広告を表示します。  
広告表示後、もう一度広告を表示するためには`3.アプリ起動時広告の読み込み`を行う必要があります。  
広告には有効期限が設定されている場合があり、広告読み込み完了後に一定時間が経過すると広告表示ができない場合があります。読み込み完了後にcanShow()を呼ぶことで広告表示可能か判別することができます。

```java
if(adstirAppOpenAd.canShow()){
    adstirAppOpenAd.show();
}
```

## アプリ起動時広告の実装例
ここではApplicationを拡張したMyApplicationクラスを作成して、アプリ起動時広告の実装例を記載します。  
広告の読み込み完了後、アプリ復帰時に広告を表示します。  

### ライブラリの追加
アプリケーションの復帰の判定に`androidx.lifecycle:lifecycle-process`を使用しているため、アプリケーションレベルのbuild.gradleに`androidx.lifecycle:lifecycle-process`を追加します。
```groovy hl_lines="1 2 3 4 6"
dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.webviewsdk:adstir-webviewsdk:${adstir_version}"
    implementation "androidx.lifecycle:lifecycle-process:2.8.6"
}
```

### 実装例
```java
import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.lifecycle.Lifecycle;
import androidx.lifecycle.LifecycleEventObserver;
import androidx.lifecycle.ProcessLifecycleOwner;
import com.ad_stir.appopenad.AdstirAppOpenAd;
import com.ad_stir.appopenad.AdstirAppOpenAdListener;

public class MyApplication extends Application implements Application.ActivityLifecycleCallbacks {
    private AdstirAppOpenAd adstirAppOpenAd;
    private final AdstirAppOpenAdListener listener = new AdstirAppOpenAdListener() {
        @Override
        public void onLoad(int spot_no) {
            // 広告の読み込みが完了した時の処理を記述できます。
        }
        @Override
        public void onFailed(int spot_no) {
            // 広告の読み込みが失敗した時の処理を記述できます。
        }
        @Override
        public void onStart(int spot_no) {
            // 広告が表示された時の処理を記述できます。
        }
        @Override
        public void onStartFailed(int spot_no) {
            // 広告の表示に失敗した時の処理を記述できます。
        }
        @Override
        public void onClose(int spot_no) {
            // 広告が閉じられた時の処理を記述できます。
        }
    };

    private final LifecycleEventObserver lifecycleEventObserver = (lifecycleOwner, event) -> {
        if (event == Lifecycle.Event.ON_START) {
            showIfAvailable();
        }
    };

    @Override
    public void onCreate() {
        super.onCreate();
        // Activityのライフサイクルのコールバックを設定します
        registerActivityLifecycleCallbacks(this);
        // ライフサイクルイベントのオブザーバを設定します
        ProcessLifecycleOwner.get().getLifecycle().addObserver(lifecycleEventObserver);
    }

    // アプリ起動時広告の初期化を行います
    private void initAd(Activity activity) {
        if (adstirAppOpenAd == null) {
            adstirAppOpenAd = new AdstirAppOpenAd(activity, "メディアID", 枠No);
            adstirAppOpenAd.setAdstirAppOpenAdListener(listener);
        }
    }
    // アプリ起動時広告の読み込みが完了している場合は表示、そうでない場合は読み込みを行います
    private void showIfAvailable() {
        if (adstirAppOpenAd.canShow()) {
            adstirAppOpenAd.show();
        } else {
            adstirAppOpenAd.load();
        }
    }

    @Override
    public void onActivityStarted(@NonNull Activity activity) {
        initAd(activity);
    }
    ...
}

```

### AndroidManifestの設定
作成したMyApplicationをAndroidManifestのapplicationタグに設定します。
```xml hl_lines="1 2 4 5"
<application
    ...
    android:name=".MyApplication" >
    ...
</application>
```

## ライブラリ詳細

[APIリファレンス](../api/index.md#アプリ起動時広告)をご覧ください。