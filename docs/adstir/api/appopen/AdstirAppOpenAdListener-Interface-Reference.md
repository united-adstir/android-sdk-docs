# AdstirAppOpenAdListener Interface Reference

アプリ起動時広告の各イベントを通知するリスナーです。

## Methods

### onLoad
広告読み込み完了時に呼び出されます。

```java
public void onLoad(int spot_no)
```

* Parameters

|パラメータ||
|---|---|
|spot_no|枠No|

### onFailed
広告読み込み失敗時に呼び出されます。

```java
public void onFailed(int spot_no)
```

* Parameters

|パラメータ||
|---|---|
|spot_no|枠No|

### onStart
広告表示開始時に呼び出されます。

```java
public void onStart(int spot_no)
```

* Parameters

|パラメータ||
|---|---|
|spot_no|枠No|

### onStartFailed
広告表示失敗時に呼び出されます。

```java
public void onStartFailed(int spot_no)
```

* Parameters

|パラメータ||
|---|---|
|spot_no|枠No|

### onClose
広告が閉じられる時に呼び出されます。


```java
public void onClose(int spot_no)
```

* Parameters

|パラメータ||
|---|---|
|spot_no|枠No|
