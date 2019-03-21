# 2日目

## What's New in Swift
Hall 2 — 9:00 AM to 9:40 AM

### open source

 -  600コントリビュータ
 - 18kプルリク
 - Community-Hosted CI
 - forums.swift.org
 - Related Projects
 - docs.swift.org
 - いろんなカンファレンス
 - 6/8 try swift san jose
 - swift5
 Binary compatibility with feature swift compliler releases
 swift runtime xxx

### swift4
 - faster builds
 - SDK improvement

source compatibility
一つのコンパイラで3つのモード swift3, 4, 4,2
マイグレーションサポート
SDK changes
update important framework API
Trajectory with source compatibility

Faster
Wは1.6倍
firefoxで2.1倍

speed up debug build
compiration pipeline optimized to redule xxx

コンパイルモードと最適化レベル

Compiration mode
デフォルトはIncremental、release はwhole module
debugではincrementalを使おう

参照カウンタの話 calling conventionを変えた
今までは無駄が多い
最後に解放

Small String

Reduced Code Size
最適化レベル
Optimize for Size
-Osize
コードサイズが10%-30%減、実行パフォーマンスが5%ダウン

## new language feature

Swiftエヴォリューションのプロセス
導入されたプロポーザル

Collection of enum cases
CaseIteratableプロトコル
allCasesで全てのケースを取得できるように

Conditional Conformance
All Array Equatable

Conditional Comformance allows composition

Equatableとhashableのシンセサイズ
Eitherで型パラメータが両方Equatableのとき、Hasshableのとき

hashableの強化
???演算子ってなに？
Hash combinding functions are hard
magicが多い
パフォーマンスもNG
inout Hasher

新しいハッシュアルゴリズム
クオリティとパフォーマンスのバランス
何かのマクロSWIFT_DETERMINISTIC_HASHxxx

乱数生成
ARC4RANDOMでなくInt.random(in 0 ..< 10)
float

コレクション
randomelement()

RundomGeneratorProtocol

プラットフォームのコンディションチェック

#if os(iOS)でなくcanImportUIKit)が使えるように

hasTargetEnvironmental(simurator)

#warning

Mental Model
IUO
オプショナルの暗黙アンラップの話
Int!

swift.org/blog/iuoで詳しく

SE-0176
https://github.com/apple/swift-evolution/blob/master/proposals/0176-enforce-exclusive-access-to-memory.md
Enforce Exclusive Access to Memory
メモリへの排他アクセスの強制
コンパイルエラー
クロージャでのキャプチャの例

リリースビルドで動的チェックが利用できる

## What's New in Cocoa Touch
Hall 2 — 10:00 AM to 10:40 AM

フレームワークの更新（パフォーマンス）
APIの強化
siriショートカット

パフォーマンスの強化（スクロール、メモリ、オートレイアウト）
スクロールとcpu
UITableViewのセルの読み込みコスト
UITableviewのプリフェッチ
prefetchRowAt
cancelPrefetchingForRowsAt
従来よりもっと賢いバックグラウンドプリフェッチのスケジューリング
CPUパフォーマンス

メモリ
メモリはパフォーマンス
Free / Your App / Other App and System
小さいリクエスト（free領域を使う）
大きいリクエスト（Other App and Systemを使う）
Automatic Backing Store
375*250@3x*64bpp = 2.2 megabytes
グレースケールの写真でも同じ
バッキングピクセル
グレースケールなら8bppで8分の1のメモリで済む
デフォルト設定でこうなる

AutoLayout
デフォルトで早くなる
シンプルなベストプラクティス
独立した兄弟関係のViews
Viewの個数に対し線形に増えていく、ios12はよりパフォーマンスが良い

独立していない兄弟関係のView
線形に増えず、増加曲線で増えるがiOS12は線形（Nested Viewsも同じ）

Swiftication

Nesting
Types
Constants
FUnctions

Nested Types

UIApplecationStateがUIApplecation.Stateに
UITabBarItemPositioning
NSNotification
UIFloatRangeZero
UIFLoatRangeInfinite

UIEdgeInsets
insetBy()
UIImage
image.pngData()

StringConversion
NSStringFrom[]FromString
Codableに対応
CGPointなどをJSONにエンコード、デコードできる

NSSecureCoding
新しいAPI

APIの強化
Notifications
Interaction
Grouping
Setting

メッセージの通知に対するアクション
通知のグルーピング

APIで設定が可能（アプリの設定に飛ばすなど）

Messages Apps
MSMessageAppPresentationContextMessages

automatic password
security code

キーチェーンにパスワード
パスワードを保存するダイアログ
パスワードの生成

確認コードがメッセージから取得できるので、メッセージにきりかえなくてもよい

Safe Area

Siri Shortcuts
NSUserActivity
Intents

ハンドオフとspotlightと同じAPI
eleidgebleForePrediction = trueをセットする

カスタムインテント

ショートカットを結合

## Automatic Strong Passwords and Security Code AutoFill
Hall 1 — 11:00 AM to 12:00 PM

パスワードはpain
セキュアでない
強くてユニークなパスワードをサービスごとに変える必要がある

Demo（shiny）
アカウントを作ってログイン
サジェステッドユーザーネーム（メアド）
パスワード欄タップでパスワードが自動生成
ログインの入力項目がサジェストされる
verifyも1タップで

password autofill
automatic strong password
securitycode AutoFill
federated authentication
new password management feature

associated domain
アプリ間で共有するのに重要

entitlememnt設定

UITextView

WKWebViewもサポート

Extensionも開発可能

infer login シナリオ
domainでチェック

Associate App with domain

Automatic Strong Passwords

UITextField
.textContentType = .newPassword
ユーザー名とパスワードは同じ画面に

パスワードフォーマットは自由に定義可能

.passwordRules = UITextInputPasswordRules(descriptor: )
verify用のツールがある

Demo（shinyの実装）
Text Input Traitsのとこで設定
content Typeをnew Passwordに

verifyツールでパスワードルールの作成
password rulesにペースト

sign-up detection

Security Code AutoFill
覚えて入力、間違えちゃう
1タップで完了、それだけ

textContentType = .oneTimeCode
システムキーボードが必要（自分で作ったものはだめ）

全てのlocalesで対応

macのサファリにも連携（iPhone）
HTMLで指定

federated authentication
他のSNS認証連携

SecureViewController

2タップで完了
1.連携ダイアログ
2.allow

ASWebAuthenticationSession
block based API

import AuthenticationService
oauth URLを指定、ASWebAuthenticationSessionにセット

hey siri show me my shiniy password

iosのパスワードマネジャーのpasswordの画面がリデザイン

tvos

## Introducing Create ML
Hall 2 — 2:00 PM to 2:40 PM

mlmodelをどうやって準備する？
1.公開されているものをダウンロードするか
2.自分でつくる

createML
swiftで書かれた機械学習フレームワーク

image、text、tabular data

Workflow
 - Problem
 - Collect Data
 - Train（Create Model）
 - Evaluate
 - MLMODEL（writeメソッドを実行）

Image Classification
画像を集める
ディレクトリに分ける（ディレクトリ名がラベル）
さらに一つのディレクトリに入れる

Transfer Learning

サイズ小さく、早く作れる

Demo

GUIでやる方法
ドラッグで学習用と評価用の画像をいれるだけ
83kbのモデル

APIでやる方法
MLImageClassifierのイニシャライザでurlから読み込むことも可能
model.evaluation

Text Classification
Word Tagging

感情分析
スパム分析
トピック分析

ネガポジでディレクトリ分け
CreateMLによるテキスト分類器の作成
ポジティブな投稿だけさせるボタン

Demo
MLTextClassifierのイニシャライザ
model.trainingMetrics
model.evaluation(url: )
model.write()

Tabular Data
FatureからTargetを予測

MLRegressor
MLLinearRegressor
MLRandomforestRegressor

## Getting the Most out of Playgrounds in Xcode
Hall 3 — 3:00 PM to 3:40 PM

import PlaygroundSupport
LiveView

MarkUp

```
//:
//:
//: # Heading1
//: ## Heading2
//: ### By: Heading3
//: aa *red*
//: aa **red**
//: aa `red`
//: 1. item1
//: *. item2
//: [this is link](https://---)
//: [1]: reference
//: [Previous](@previous)
//: [Next](@next)
//: [Formatingtext

/*:

*/
```

//: ![alternate text](hoge.jpeg 2hover title")

Running Step by Step

1行ずつコードの実行ができる
shift+returnで現在の行を実行
青い行は実行準備ができている
respond to live data
違う値で再実行

Demo

五目並べゲーム
実行後に新しい行にコードを追加してさらに実行

Step by Step Suggestions

Advances Techniques

Custom playground display Convertible
CustomStringConvertibleプロトコル
CustomPlaygroundDisplayConvertibleプロトコル
Textual、Graphical
UIKitではCustomPlaygroundDisplayConvertibleがすでに実装されているものも

importing your code
ファイルの設定

Demo

ここで眠気がMAXに。。。
別のKeyboardフレームワークをimportする

## Strategies for Securing Web Content
Executive Ballroom — 4:00 PM to 4:40 PM

Secure Transport
labが長引いたので聞けず

Cross-origin lockdown
違うドメイン
Cross-origin image
Cross-origin script function onliad() {}
Cross-origin iframe

same-origin policyがガードしてしまう
簡単な方法はtabを分ける

Cross-origin lockdown

subresource integrity
<script src="..." integrity="sha256-...">
</script>

integrityがチェックされる?

content security policy
HtTP responseヘッダ
Content-Security-Policy:
  default-src 'self'; // No inline
  script-src cdn.example;
  frame-src social.example;
  frame-ansestors news.example;

Set-Cookie:
  auth=abc...123; httpOnly; // HttpOnly cookies
  SameSite=strict // SameSite cookies

Cross-Origin-Window-Policy: Deny

Cross-Origin Attack
クロスサイトスクリプティング
フォームの中にjsを書く

default-src 'self'; があるのでインライン実行できない

Compromised CDN
integrity check sum で弾けるs

クロスサイトフォージェリ
SameSite=strictでガードできる

speculative execution defined
// 推論的な

WKWebView

WebKit
Architecture

UIWebView vs WKWebView
WKWebView is out of process
なんかプロセスが一緒か分かれてるかどうかの違い??

frame-ansestors 'none'

speculative execution attacks

Cross-Origin-Resource-Policy
Cross-Origin-Resource-Policy: Same

Window Control Attacks

https://webkit.org/blog/

## Introduction to Siri Shortcuts
Hall 2 — 5:00 PM to 6:00 PM

Siriがアプリの機能を見えるようにする

ショートカットの適用方法
ショートカットの定義
Donate Shortcuts（Extensionに移植？）
Handle Shortcuts

ショートカットはいつでも実行できるべき、何度も実行したくなるものであるべき
APIはNSUserActivityとIntents（SiriKit）

アプリを起動
アプリを起動せずにインライン実行

Info.plistでアクティビティのタイプを定義
isEligibleForSearch = true
isEligibleForprediction = true

Intents
カスタムインテントの作成
ファイルを追加（SiriKit Intent Definition File）

商品名や数、届け先、オプションなどの引数を定義（数とタイプ）
Supports background execution

インテントに対し自動でコードが生成される

Intents Extension
-continueUserActivy

Demo

import Intents

INInteraction
.donate

Settings

サジェストの最適化
サジェストはユーザーのショートカットの実行履歴からパターンを予測して生成される

日付などは今日、昨日など相対的に指定できるようにすると便利
良いショートカットはタイトル、サブタイトル画像をわかりやすく表示する

テスト
ショートカットのテストは開発者設定をonにする
スキームにintentのクエリを指定してテストすることができる

delete donations

NSUserActivityPersistIdentifierent
ININteraction.delete / deleteAll

Media Intent

# Xcode Open Lab

## CococaPodsライブラリに依存したCarthageライブラリの配布方法
https://github.com/shtnkgm/CarthageLibraryIncludePodsLibrary

利用するアプリ側のプロジェクトで設定
1. SVProgressHUD.frameworkをFrameworkグループにドラッグで追加
2. Build Phasesで「New Copy Files Phase」
3. DestinationをFrameworksに変更
4. 先ほどコピーしたSVProgressHUD.frameworkをNameのところにさらにドラッグで追加
5. クリーン&ビルド

## GPUImageのCarthageエラー
https://github.com/BradLarson/GPUImage/issues/2573

分からないとのこと

## 利用していないクラス、関数、画像の検知（コンパイル時にwarningを出したい）

現在はSwiftではこの機能はない
BugReportに出すことで機能追加されるかも
