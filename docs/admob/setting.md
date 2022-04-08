# AdMob配信設定
AdMobの配信設定をご自身でされる場合は営業担当にご連絡後、下記の手順で設定してください。

1. AdMob管理画面の`メディエーション グループ`の`ウォーターフォール`から`カスタムイベントを追加`を選択してください。  
1. ラベルは自由に設定してください。  
1. 手動 eCPMはadstirのレポートから判断して設定いただくか営業担当までご相談ください。  
1. Class NameとParameterは下記の各広告フォーマットの設定をご利用ください。

## バナー広告/アダプティブバナー広告
通常バナーアダプタは一部の広告が配信できませんが、広告が在庫切れの際にAdMobにパスバックすることができます。  
フィラー用のバナーアダプタは広告が在庫切れの際にAdMobにパスバックができない場合があります。  

### 通常バナーアダプタ
| Class Name | Parameter | Parameter設定例 |
| :--- | :--- | :--- |
| com.ad_stir.webview.AdstirWebViewApiMediationAdapter | \{"mediaId":"adstirメディアID","spotNo": adstir枠No,"width": 広告枠の横幅,"height":広告枠の高さ\} | {"mediaId":"MEDIA-XXXXX","spotNo": 1,"width": 320,"height":50} |

width, heightにはadstirで作成した広告枠の広告サイズを設定してください。

### フィラー用バナーアダプタ
| Class Name | Parameter | Parameter設定例 |
| :--- | :--- | :--- |
| com.ad_stir.webview.AdstirWebViewMediationAdapter | \{"mediaId":"adstirメディアID","spotNo": adstir枠No,"width": 広告枠の横幅,"height":広告枠の高さ\} | \{"mediaId":"MEDIA-XXXXX","spotNo": 1,"width": 320,"height":50\} |

width, heightにはadstirで作成した広告枠の広告サイズを設定してください。

## ネイティブ広告
| Class Name | Parameter | Parameter設定例 |
| :--- | :--- | :--- |
| com.ad_stir.nativead.AdstirNativeMediationAdapter | adstirメディアID,adstir枠No | MEDIA-XXXXX,1 |

## 動画リワード広告
| Class Name | Parameter | Parameter設定例 |
| :--- | :--- | :--- |
| com.ad_stir.videoreward.AdstirVideoRewardMediationAdapter | \{"mediaId":"adstirメディアID","spotNo":adstir枠No,"spotNos":[adstir枠No,adstir枠No2]\} | \{"mediaId":"MEDIA-XXXXX","spotNo":1,"spotNos":[1,2]\} |

spotNosにはアプリで利用する動画リワード/全画面インタースティシャル広告の枠Noを全てカンマ区切りで設定してください。

## 全画面インタースティシャル広告
| Class Name | Parameter | Parameter設定例 |
| :--- | :--- | :--- |
| com.ad_stir.interstitial.AdstirInterstitialMediationAdapter| \{"mediaId":"adstirメディアID","spotNo":adstir枠No,"spotNos":[adstir枠No,adstir枠No2]\} | \{"mediaId":"MEDIA-XXXXX","spotNo":2,"spotNos":[1,2]\} |

spotNosにはアプリで利用する動画リワード/全画面インタースティシャル広告の枠Noを全てカンマ区切りで設定してください。