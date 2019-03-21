# 4日目

## Building Faster in Xcode
Hall 2 — 9:00 AM to 9:40 AM

Build your apps faster in Xcode 10. Learn how to structure your projects and tweak your code to take full advantage of all processor cores. Whether you've made a few small code changes you want to give a try, or you're building your full app for release, these techniques will cut the time it takes to build a running app.

Xcode 10でアプリケーションをより速く構築する。すべてのプロセッサコアを最大限に活用するために、プロジェクトを構築し、コードを微調整する方法を学びます。 試してみたいコードを少し変更した場合でも、リリース用の完全なアプリを構築している場合でも、実行中のアプリケーションをビルドするのにかかる時間は短縮されます。

 - パラレル実行
   - ターゲットの依存関係グラフを元に、ビルドエラーを出さないようにターゲット単位でパラレルで実行できる
   - スキームエディタのbuild Options（パラライズドビルド、find implicit dependency）
   - ビルドフェーズのlink binary with libraries、Target dependenciesに依存関係を設定
   - テストもターゲット毎にテストターゲットを分割すべき
   - Dependency Exposeを減らす（Code Genに依存させる）
   - 不要な依存を検証する
   - Xcode10では依存関係があっても、早めに後続のターゲットのビルドが開始する（必要な分だけ待つ）
   - Run ScriptではXcode10からInput File Listsが追加できるようになった
   - xcfilelist: Run ScriptのInput filesとOutpu filesの中身を改行区切りで羅列できるファイル
   （ドキュメントを用意したので見ましょう / Run a Shell Script）
   - 循環依存の検知（これもドキュメントを用意した）
 - ビルド時間を測る
   - 標準でもビルドログにでるようになった？
   - showBuildTimmingSummary
 - ソースコードレベルの改善
   - compilation modeのwhole module modeをdebugではoffにしよう
   - incrementalの指定が可能に
   - 複雑な表現を対処する
     - 複雑なプロパティで型を明示する
     - 複雑なclosureでは型を明示、複雑な条件分岐もswiftyに書く（型推論に時間がかかる場合はコンパイルエラーになる）
     - AnyObjectのメソッド実行には時間がかかる、プロトコルに置きかえよう
   - Swiftの依存関係を理解する
     - 差分ビルドはファイル単位
     - 関数の中身の変更は他ファイルには影響しない、型定義は影響する
     - Targetの依存関係も差分ビルドに関係する（上位の変更は下位に影響しない、その逆は影響する）
   - ObjC/Swigftの共存するプロジェクトのヘッダ生成を理解する
     - Objcのヘッダ→ブリッジングヘッダ、Swiftコード、Swiftインタフェースから自動生成したObjCヘッダ→Objc実装ファイル
     - privateを使ってインタフェースを非公開にし、自動生成ヘッダを小さくしよう
     - Notificationでも@objcで公開しなといけない場合もprivateをつけるか、ブロックベースのAPIと使う
     - Swift4への移行（Edit > convert > to curent swift syntax）
     - Swift3 @objc intferenceをオフにし、暗黙の@objc推論を減らす
     - ブリッジングヘッダを小さくする、カテゴリ文法を使ってヘッダでなく、実装側にヘッダのimportを書く

## Optimizing Your App for Today’s Internet
Hall 3 — 10:00 AM to 10:40 AM

Learn what Apple has been doing to help your app get the most out of the network with the least effort. Let Apple’s networking APIs do the heavy lifting for you. Learn best practices for getting top networking performance from your app using the URLSession APIs.

 - 今日のネットワーク情勢
   - 40億の人がインターネットを利用している
   - 2G回線ユーザーはまだ多い
   - 各国のIPv6の利用可能状況
   - IPv6やECNをサポートしよう
 - Multipath TCP（MPTCP）
   - フェイルオーバー接続が高速
 - TCP Fat Open（TFO）
   - TCPのハンドシェイク時間を削減
 - Quick UDP Internet Connection（QUIC）
   - comming soon
 - DNSのパフォーマンス
   - Optimistic DNS （CloudKitで利用されている）
 - SCNetworkReachabilityを避ける
  - waitsForConnectivityを利用する
 - TLS1.3
   - セキュリティが改善
   - 接続確率時間を削減
   - mobileconfig（ios）やターミナルコマンド(macos) で利用できる
 - 証明書の透過性（Certificate Transparency）
   - 新しいポリシーcomming soon
 - Bonjour Conformance Testing
 - APIの選択
   - BSD Socketsを直接
   - サードパーティライブラリを利用（BSD Socketsを利用する）
   - URLSession（Network.frameworkを利用する）
   - Network.frameworkを直接利用する
   - BSD Socketsを避けること
 - URLSession
   - ネットワークパフォーマンスはほとんどのアプリ重要な項目
   - レイテンシー
     - HTTP1.1の問題
       - コネクション確立、リクエスト、アイドル状態、レスポンス
       - リソース毎にコネクション確立をしてしまうので時間がかかる
       - シングルコネクションでも時間がかかる
     - HTTP/2
       - シングルコネクションでHTTP1.1よりも高速
       - HTTP1.1に比べアイドル時間が短い
       - HTTP/2にアップグレードしよう
       - クライアント側の変更はない
     - HTTP/2 Connection Coalescing
       - コネクションの再利用
       - サブドメインは違ってもベースドメインが一致していれば共通のコネクションを利用
       - ios12/モハべで利用
   - スループットの最大化
     - リクエストサイズを減らす
       - HTTP CookieはHTTP/2ヘッダで圧縮される
       - HTTP圧縮（http/httpsではGzip、Brotliはhttpsのみ）
   - レスポンシブネス
     - QoS class
       - URLSessionはQoS-aware
       - task.resume()でQoSがキャプチャされる
     - Network Service Type（New）
     - 全てのセッションでwaitsForConnectivityを有効化する
     - task.cancelはもう不要    
   - システムリソース
     - バックグラウンドセッションを使う（wwdc2014）
     - URLSessionconfiguration.background(...)
     - キャッシュを賢く使う
       - willCacheResponseデリゲートメソッド

## Creating Custom Instruments
Hall 1 — 11:00 AM to 12:00 PM

Understand how custom instruments are useful and when they should be used. Get an in-depth view of the architecture of custom instruments and how to create them. Understand the attributes of a good instrument. Dive into advanced modeling and how to use the CLIPS language.

  - アーキテクチャ
    - インストゥルメントはStandardUIとAnalysisCoreで開発
    - 画面上部のGraphsと画面下部のDetail Views（AnalysisCoreからデータを取得）
    - Tables（schemaとattribute）
      - tick schemaの例
  - Demo
    - 毎秒timestampを出力するカスタムインストゥルメントを作成するデモ
    - Xcodeでプロジェクトを新規作成（インストゥルメントパッケージテンプレ）
    - .instrpkgファイルに設定をXML形式で記述
     - <import-schema>、<instrument>
    - Instruments > Preference からパッケージを確認
    - カスタムインストゥルメントのテスト
  - UI
    - Plot
    - Automatic Treatment
    - Plot Template
    - histogram（count, sum, mini, max, average）
  - Details
    - List
    - Aggregation（Columnsはfunction）
    - Call tree
    - Narrative
    - Time slice
  - データの加工プロセス
    - 1. Reduce
    - 2. Serach
    - 3. Optimize
  - Binding Solution
  - Schemes
    - 100を超えるスキーマがalready
    - link build settings
    - Modelers
  - Automatic Modelers
    - os-signpost-interval-schema
  - traiblazerアプリでos_signpostのデモ     
    - 画像のダウンロード時間、数、名前とサイズが出力される
  - Production System
  - Advanced Instrumentのデモ
    - 通信のアンチパターンを検知する  
    - CLIPSファイル
    - 謎のスクリプト"defrule"は右上から追加できる
  - ベストプラクティス
    - 1個以上のインストゥルメントを書く
    - Immediate modeは難しい
    - last 5s modeは最も有効

## User Interface Design Lab

 - アプリの体感速度を上げる方法
 - ガイドラインに沿っていないデザイン、bad UIの場所があれば
 - 商品詳細画面のUI（表示要素が多い）

商品名はもっと大きく
説明テキストがちいさい
だんだん小さく
重要な情報は上の方に
カテゴリごとに大きいフォントがある
テーブルデバイダーもよい
商品情報は省略してもいいのではないか
情報を全部入れるのは反対、知りたい方法にアクセスできるように

商品詳細をみるのはどっちかでいいのではないか
商品を見比べることをしたいので、それができるような体験にした方が良い
特定の商品についての情報は

検索二つあるのは混乱する
上の検索をなくすかお気に入りの検索にするなど
プルダウンで検索を出す方法もある

検索でなくカテゴリタブにしたらどうか
もっとユーザーが必要なもの

検索履歴が見れるのはよい

ラベルだけでも表示する
フレームだけをだすのがよい
もちろんUIで工夫することも大事だが、サーバー側を早くする方が良い

大きいものは早く出す
ユーザーがスクロールを止めた時に他の情報をロードさせる
カートボタンは固定なら初めから出しておく


## Embracing Algorithms
Hall 3 — 2:00 PM to 2:40 PM

When you imagine building a new app, what do you think about? Models, views, and controllers deserve their prominent place in the design process, but we don't often give the same attention to the underlying work our apps need to do. Understand how to identify and optimize the algorithms in your app, and discover how implementing algorithms as generic protocol extensions results in efficient, effective, and maintainable code.

UI Design Lab優先したので行かず。
あとで動画見る。

## Vision with Core ML
Hall 1 — 3:00 PM to 3:40 PM

Using Core ML models in Vision makes the creation of powerful Computer Vision applications easy. Learn how easy it is to use custom trained classifiers and object recognition models in a live camera capture. In addition, you'll learn about the latest additions to the Vision Framework along with a deeper dive into some its fundamentals.

 - カスタム画像分類
   - CreateMLで学習
   - フォルダ名を分類のラベル名にする
   - カテゴリにつき最低10、多い方が良い
   - バランスの悪いデータセットは学習が難しい
 - 転移学習
   - 学習済みのモデルで始める
 - Vision FeaturePrint.Scene
   - 1000以上のカテゴリを分類可能
   - カスタムモデルの容量が小さい（KBオーダー）
   - アップル端末に最適化
   - CPU負荷が高いので必要な時だけ分類をさせる
   - カメラが動いていない、対象が動いてない条件で利用する
   - 分類は間違うのでバックアッププランを（バーコード読み取りなど）
   - 学習用のデータは違う背景で撮ったりする
 - 重い分類処理には非同期にすること
 - CoreMLをなぜ使わないか
   - xxx聞き取れず
 - YOLO（you look only once）
   - label.firstで最も信頼度の高いラベルの取得
   - boundingBoxで矩形取得
 - Vision Fundamental
   - 画像の回転について
   - 原点はlower-left
   - 信頼度（0.0~1.0）
   - 信頼度1.0が必ずしも正しいとは限らない

## Optimizing App Assets
Hall 1 — 4:00 PM to 4:40 PM

Learn how to use assets to bring visually compelling and data efficient artwork to your apps, leveraging new features in iOS 12. Gain insight into organizing, optimizing, and authoring artwork assets by using asset catalogs to their fullest. Learn techniques to better streamline workflows between designers and developers. Ensure better app delivery and a smaller footprint, maximizing target audiences of your app with full artwork asset fidelity.

アセットを使用して、アプリに視覚的に魅力的でデータ効率の良いアートワークをもたらし、iOS 12の新機能を活用する方法を学びましょう。アセットカタログを最大限に活用して、アートワークアセットの整理、最適化、 デザイナーと開発者の間のワークフローを合理化するテクニックを学びます。 より優れたアプリデリバリとフットプリントの縮小を実現し、完全なアートワークの資産忠実性でアプリのターゲットユーザーを最大限に活用できます。

 - 画像の圧縮
   - Compression typeを選択できる
     - Automatic Image Packing
       - 複数の画像を1つの画像にすると80%の容量削減
     - Lossy Compression
     - High Efficiency Image File format（HEIF: wwdc17）
       - JPEGよりもよい圧縮率
       - 透過画像をサポート
       - 他の画像形式からの自動変換
     - Lossless compression
       - シンプルな画像と複雑な画像
       - Apple Deep Pixel Image Compression
         - 最適な圧縮アルゴリズムを選択
         - 15-20%のサイズ改善
         - 現行のLossless compressionに比べ、デコード時間も早くなった
     - Deployment target and app thinning
       - 従来の方式と比べiOS12未満のOSもサポート（Thinnningは最新OSのみ）
       - ガレージバンドの各デバイスでのアプリサイズ、iOS12では11-23%サイズを削減
 - Design and Production
   - 多くの画像を扱うのは大変
   - 色の管理
     - Color Profile
     - ビルド時にアセットカタログがカラーマッチを行う
     - 全てのデザインファイルで一貫した色の設定を行える
     - wide color(wwdc16)
   - 伸縮する画像
     - slicing
   - Vector assets
     - PDF形式で@1x、@2x、@3x全ての解像度に対応
     - Preserve Vector Dataにチェックをいれると動的にリサイズ
   - Design for 2x
     - 最も主流な解像度だが、ストロークはまだぼやけてみえる
     - デバイスのピクセルのならびに合わせて頂点をスナップさせる
   - Hinted Assets
 - Assetsの整理
   - Bundles
     - 画像だけのバンドルを作成
     - バンドル単位でユニークとなる
   - Namespace
     - Provide Namespaceにチェック
 - Deploy
   - App thinning
     - デバイス単位で最適な画像のみ配布
   - Performance Classes
     - NSDataAsset
   - Graphics Classes
     - Metal
   - Sprite Atlases
     - SpriteKit.framework - SKTextureAtlas
     - 非同期読み込みが必要


## Advanced Debugging with Xcode and LLDB
Hall 2 — 5:00 PM to 6:00 PM

Discover advanced techniques, and tips and tricks for enhancing your Xcode debugging workflows. Learn how to take advantage of LLDB and custom breakpoints for more powerful debugging. Get the most out of Xcode’s view debugging tools to solve UI issues in your app more efficiently.

高度なテクニック、Xcodeのデバッグワークフローを強化するためのヒントを学んでください。 LLDBとカスタムブレークポイントを活用してより強力なデバッグを行う方法を学びます。 Xcodeのビューデバッグツールを最大限に活用して、アプリ内のUIの問題をより効率的に解決してください。

 - Swiftのデバッグの信頼性がXcode10で改善
   - ASTコンテキストからモジュールの取得に失敗するエラーを修正
   - Swiftの型解決エラーを修正
 - ライブデバッグ & 気に入りのデバッグTips
   - breakpointでDebugタブを表示
     - Edit Beheiviorで設定
   - poで値を参照
   - expression aaa = bbbで値を書き換え（インジェクトコード）
   - ブレイクポイントアクション（expression）で常に値を書き換え
   - リビルドせずにブレイクポイントアクション（expression）で処理を変更
   - シンボリックブレイクポイント（objc形式で書く）[UILabel setText]
   - po $arg1（アセンブリフレームの引数）
   - po $arg2
   - po $arg3
   - シンボリックブレイクポイントアクション breakpoint set --one-shot true --name "-[UILabel setText]"
   - ブレイクポイントの右側のバーをずらす1
   - thread jump --by 1で処理を1行飛ばしてexpressionでインジェクション
   - CustomDebugDescriptionString
   - p
   - Watchpoints（値が変わった時にトリガーされるブレイクポイント）
   - po self.viewでメモリアドレスを取得 = expression --object--description
   - po self.view.recursiveDescription()
   - expression -1 objc -0 -- [self.view recursiveDescription]
   - expression -1 objc -0 -- [`self.view` recursiveDescription]
   - po メモリアドレス
   - command alias poc expression -1 objc -0 --
   - po unsafeBitCast(メモリアドレス, to: view.self).center
   - expression CATransaction.flash()
   - open nudge.py
   - command script import ~nudge.py
   - nudge 0 -5 メモリアドレス
   - nudge 0 1 view
   - nudge 0 2
   - frame variable <name>
 - 最後にtipsのまとめと概要あり
 - Viewのデバッグ
   - debug view ヒエラルキー
   - show clip contentでクリップされたコンテンツを表示
   - `po ((NSLayoutConstlaynt *) メモリアドレス)`
   - 制約をセット
   - flash🚽
   - All Allocation Free History
   - 制約の該当行を表示する
   - 複数画面ののDVHを表示
   - DVHからシステムで指定された色かどうかを確認
   - dark modeかどうかを切り替えして両方の表示を確認
 - こちらも最後にまとめあり
