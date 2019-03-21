# 3日目

## What's New in Testing
Hall 2 — 9:00 AM to 9:40 AM

コードカバレッジ
テストの選択と順番

Xcode9.3
xccov

パフォーマンスと精確さ
Xcode9に比べ、Xcode9.3ではコードカバレッジの表示が早く、ファイルサイズも小さくなった
コードカバレッジでターゲット毎の有効・無効が選択可能

xccov
コマンドラインツール
xccovereportでカバレッッジレポート
xccovearchive
xcodebuild -resultbundle

xcrun xccove view --json xxx.

Source Editor
Editor > Show Code Coverage

Demo

スキーム設定でコードカバレッジを有効化、ターゲットも選択可能
パーセントでターゲットごとのコードカバレッジを確認
ファイルごとのカバレッジを確認し、カバレッジが低いところを改善
テストを追加して再度テストを実行、カバレッジが改善されることを確認

テストの選択と順番

スキームでのテストの選択
"Tests to skip", "Tests to run"
新しいテストを自動で追加

テストの順序
デフォルトはアルファベット順
暗黙的なテスト順序に対する依存が生まれる可能性がある

ランダムモードを追加
毎回実行順序をシャッフルする
スキームエディタで変更できる

パラレルテスト
テスト実行が終わるのを待つのはダルい
複数のdestinationを指定可能に
xcodebuild Tests
  -destination 'xxx'
  -destination 'xxx'
  -destination 'xxx'

xcodebuildでのみ有効
single destinationでのパラレル化
テストアーキテクチャ
ユニットテストはテストバンドルでユニットテストを実行
UIテストはUI Test Runnnerでアプリを実行

パラレルで複数のRunnerを実行
テストクラスごとに平行実行（複数のRunnerでテストクラスを消化）

シミュレータでのパラレルテスト
シミュレータをクローン、各シミュレータのRunnerでテスト実行
オリジナルのシミュレータはテスト実行中は使われない
macOSでのパラレルUITestは非サポート

テストレポートで各テストメソッドの実行時間を確認
右上で合計のテスト時間を確認
Execute in パラレル にチェック
14sが5sに

UITest
iPhoneXを3台同時実行
Log

xcodebuild  
  -parallel-testing-worker-count n
  -parallel-testing-enabled YES | NO

Tips
長いテストクラスは複数クラスに分けよう
パフォーマンステストは別バンドルでパラレルは無効化しよう
もうひとつあったけどメモれず

## Building for Voice with Siri Shortcuts
Hall 2 — 10:00 AM to 10:40 AM

どのようにショートカットを追加するか
SoupChef（サンプルアプリ）
siriの設定でショートカットを作成
「soup time」というだけでスープを注文

カスタムレスポンス
カスタムレスポンスの種類
xxx
Success
Information
Error
カスタムレスポンスの適用
カスタムインテントを定義する
インテントのカテゴリを設定
レスポンステンプレートを設定
レスポンスプロパティを宣言
レスポンステンプレートStringを設定

INIntentResponseクラスを継承してカスタムレスポンスを作成
カスタムインテントのハンドラクラスを作成、どのレスポンスを返すか判定
インテントのハンドラクラスを作成

ショートカットのカスタムUIを与える
ロックスクリーン、spotlightで表示
レシート表示

demo
カスタムインテントレスポンスの作成
プロパティとテンプレートを作成
intentハンドラでどのレスポンスを返すかコーディング

ベストプラクティス
NSUserActivity or intents（バックグラウンド、インライン）

title
subtitle
image
suggested invocation phrase

文章の形式で
重要な情報を含むように
intentに動詞を含む
アプリ名は不要
重複した情報を入れない
キーワードのみだと何をするのか分からない

NSUserActivityでのコード例 suggestedInvocationPhrase
Intentsでのコード例
インテント定義ファイル

短くて覚えやすいようにする、へいしりは不要
「チャウダータイム」くらいシンプルに
「チャウダー食べたい」日本語w
インテント定義ファイルでローカライズもできるよ

INShortcut
sharedSuggestions

ショートカットをアプリにどう持ってくるか
Add to siri
INUIAddShortcutViewController
ショートカット一覧

## The Qualities of Great Design
Hall 2 — 11:00 AM to 12:00 PM

クオリティとは何か、専門家でも解釈は様々
not random, lot of care...
デザインにおけるcareとは何か
なぜクオリティが重要なのか

シンプルなデザイン
なぜシンプルであるべきか
即時に理解できる
気が散らず、集中できる

魅力的なデザイン
美しく、アート作品のようであること
ゲーム内でどのようにルールを学ぶか

時間を超越したデザイン
耐久性

アプリの体験
ユニークで価値がある
ポジティブな影響

テクニック
デザインは難しい
理解を深める
caricatureを書く
プロトタイピング
フィードバックをもらう
謙虚、気を配る
質問をする
コミュニケーションについて会話する

デザイナーのそれぞれの好きな色
pantone 347 www

## tech lab UIKit

UITextViewのstrong passwordのサンプルコードを作ったが、
以下のエラーが出てパスワードのサジェストがでないので相談

2018-06-06 12:56:00.214552-0700 Autofill[602:74773] [AutoFill] Cannot show ASP for app bundleID: com.shotanakagami.Autofill due to error: Error Domain=SFAutoFillHelperErrorDomain Code=2 "(null)"
→解決できなかったので、password autofillのラボで相談

Code=0の場合はシミュレータで実行していたことが原因
2の場合はappIdでassociated domainを設定していなかったことが原因

shinyのサンプルコードはあるか？
→いまのところ検索してもでてこないのでないが、
今後追加されるかも
https://developer.apple.com/search/?q=password%20autofill

UIStackViewのパフォーマンス、どんどん利用すべきか
→ケースバイケースなので一概には言えないが、
スクロールして表示するコンテンツの量が多い場合はUITableView、UICollectionViewを使う
そうでない場合はUIScrollView + UIStackViewでOK
ショッピングの商品詳細みたいな画面であればStackViewが有効

## Measuring Performance Using Logging
Hall 1 — 2:00 PM to 2:40 PM

signposts
os_log familyの一部
OSLog(subsystem: "", category: "")
os_log(...)

インストゥルメントで可視化して確認可能

特定の処理をbeginとendで囲む
os_signpost(.begin, ...)
os_signpost(.end, ...)

subsystemはバンドルidでOK
categoryはグルーピングに使う
nameはbeginとendで同じものを指定する

非同期な処理のインターバルの計測
OSSignpostID(log: refreshlog)
signpostIdはプロセススコープ

signpostにメタデータを付与する方法
os_log形式の文字列リテラルで渡す

インターバルでない瞬間的なイベント送信
os_signpost(.event, ...)

Signpostの有効化、無効化
OSLog.disabled

import os.signpost

インストゥルメンツ
signpostデータの可視化
Trailblazer（サンプルアプリ）

os_signで検索、インストゥルメンツを起動
レコードボタンタップ
zoom inできる

画面下半分でサブシステム > カテゴリ > name >　メタデータの順にパネルを展開できる
min avg std durationの計測結果が表示

レコーディング前にレコーディングおモードの変更
Global Options > Recoding Mode > Last n second

point of interest

## Using Grouped Notifications
Hall 3 — 3:00 PM to 3:40 PM

通知をグルーピングすることで、よりたくさんの通知を見ることができる
通知をエキスパンド、管理、全てクリアなどの操作ができる

カスタムグルーピング
UNMutableNotificationContentクラスの
threadIdentifierプロパティでグループを作成することが可能
プッシュ通知の場合もペイロードにthreadIdentifierを指定する

カレンダー、メッセージ、メールでのグルーピングの例
カレンダーアプリでは直近の予定が重要
threadIdentifier = nilの場合はデフォルトグループになりまとめられる
直近の予定はthreadIdentifier = "alerts"のグループにまとめている

重要なもの、アクションできるものはグループを分けよう

メッセージ
threadIdentifier = "michele-xxx"
threadIdentifier = "gr-xxx"

メール
メッセージよりも大量に通知が来る
アカウント、vip、スレッドごとに分けている

ユーザーの優先度や組織を尊重しよう

グループの概要を表示するカスタマイズ
そのままでは 9 more messagesなど
UNNotificationCategoryのイニシャライザでcategorySummaryFormatを指定
hiddenPreviewsBodyPlaceholderで"%u個のメッセージがあるよー!"など、テンプレのカスタマイズが可能
summeryArgumentで一番上に表示するタイトルを指定
プッシュペイロードの場合はsummary-argを指定

Podcast
summaryArgumentCount
summary-arg-count
デフォルトは1

サマリのローカライズ
NSString.localizedUserNotificationString(forKey: "xxx", arguments: nil)
ローカライズ用のplistファイルを指定

フォーマット
%u :通知の数
%@ :arguments

クイックTips
リッチなグループ通知、Extensionでなんかやる

## Intentional Design
Hall 2 — 4:00 PM to 4:40 PM

Intentional Designとするための5つの要素
1. Radical Simplification
2. Deep understanding
3. Extreme focus
4. Personal connection
5. Direct Communication

翻訳アプリ
Vanido（音程の練習アプリ）
Streaks Workout

ユーザーに判断をさせるようなものを減らす
ランダム性

ペルソナ、マーケティング調査
人々が本当に欲しいものを知ること

スーツケースのデザイン
天気アプリのデザイン
自分のためにつくられているようなデザイン

我々の経験、よくあるパターンからbad UIは生まれる
カバンにタイヤと紐をつける

メタファー
ホームアイコンはいろんなところで使われる
タブバーのホームアイコンは特定の機能を表現したアイコンにすべき
ショッピングアプリもホームアイコン使ってるな...

TinyCardsアプリ

## Practical Approaches to Great App Performance
Hall 1 — 5:00 PM to 6:00 PM

パフォーマンス問題はまず計測するところから
修正したらパフォーマンスがどの程度改善したか確認する

バグ修正
再現
デバッグ --> Profile（パフォーマンス修正の場合）
修正
繰り返す

パフォーマンスワークの種類
二つのタイプのテスト
・ユニットテスト
・インテグレーションテスト

Demo
Xcodeのパフォーマンスデバッグ
インストゥルメンツのTimeProfiler
ターゲットをXcodeに変更
フォーカスしたいエリアをドラッグ
下の部分をみる
スレッド

call treeのseparate by threadのチェックを外す
メインスレッドにフォーカス
もっとも重いバックトレース

call treeのflatten recursionにチェック
もっとも時間がかっているものを展開していく
クリックしてCharge ~を選択

call tree constraintsのminを20にする

よくある解決法
Defer
Batch
Share results
Fewer views
Direct observation
Prefer records to dictionaries

iOS写真アプリのパフォーマンスデバッグ
最初は多くの写真の表示にすごく時間がかかっていた

モーメントの起動
起動とは
Cold
Warm
Hot

Instant（500ms-600ms）
No spinner
No placeholders

100ms dyld
500ms main/UIApplicationMain

3つの原則
be lazy
be proactive
be constant

最初は3580ms

以下の処理に関してそれぞれ工夫したところの説明
データベースの初期化
ViewControllerの準備
テーブルビューデータソースの設定
ライブラリ画像の読み込み
クラウドステータスの取得

コレクション/年別の構築
スピナーなし、プレースホルダーなし、スムーズなアニメーション
be lazy
be proactive
be constant
be timely

atlasing Approach
実は一つの画像として表示している
でも3Dタッチで1枚の画像が表示される
