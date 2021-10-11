# よくある質問

## Google AdManager/AdMobでadstirの広告が表示されません

AdMobメディエーションアダプタがプロジェクトに追加されていない可能性があります。
追加されていない場合は、下記のいずれかの方法でプロジェクトに追加してください。

- Android Studioによる組み込み(build.gradle)
```groovy hl_lines="6 10"
repositories {
    google()
    maven { url 'https://cdnp.ad-stir.com/m2' }
}

dependencies {
    // 利用するadstirのSDKバージョンを設定します
    def adstir_version = "{{version.adstir}}"
    implementation "com.ad-stir.mediationadapter:adstir-admob-mediation-adapter:${adstir_version}"
}
```

- 手動組み込み
adstir SDKのzipファイルに同梱されている`adstir-admob-mediation-adapter.aar`をプロジェクトに追加してください。

## レポートに表示回数が反映されません

開発版とリリース版のパッケージ名が異なる場合、一部の提携ネットワークで実績の取得が行われないことがございます。
その際は、リリース版と同じパッケージ名に変更いただいた上でテストいただくか、開発版とリリース版のパッケージ名が異なる旨を添えていただき、レポート数値について営業担当にお問い合わせください。
