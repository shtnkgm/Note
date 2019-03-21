# 5日目

## 229_Using Collections Effectively
Hall 2 — 9:00 AM to 9:40 AM

Every app uses collections! Go beyond the basics with specific tips on how best to use indices, slices, bridging, laziness, and reference types. Gain better understanding of when to use each collection for best performance.

すべてのアプリはコレクションを使用しています！ インデックス、スライス、橋渡し、怠惰、参照型の使い方に関する具体的なヒントとともに、基本を超えて 最高のパフォーマンスのために各コレクションをいつ使用するかをよりよく理解してください。

 - protocol Collection
 - CollectionはSequenceに適合し、subscriptを実装したプロトコル
 - CollectionのExtension
 - Collectionのプロトコル階層
 - ランダムアクセスコレクション
 - SwiftのCollection
 - ArrayもSetも最初の要素はfirstで取得する
 - Collectionの2番目の要素はsliceで取得する self.dropFirst().first
 - Slices
   - Array -> ArraySlice
   - String -> Substring
   - Set -> Slice<Set>
   - Slicingは元の配列をコピーする
   - Eager Functions
   - Lazy Functions
     - Lazy Colllection<Range<Int>>
     - LazyFilterCollection
     - LazyMapCollection
     - Lazyは計算を遅延させる
     - いつLazyを利用すべきか
   - Mutable Collection
   - クラッシュするCollectionのコード
   - インデックスやsliceを保持・計算する場合は注意
   - マルチスレッドMutable Collection
     - マルチスレッドの場合、appendが正しくできない、もしくはクラッシュすることがある
     - シングルスレッドで良い場合はシングルスレッドにする
     - TSANを使う
     - イミュータブルなCollectionを使うべき
     - 可能であればキャパシティを指定する
   - 参照型コレクション
     - 参照型と値型のコレクション
     - SwiftとObjCのブリッジング
     - 二種類のブリッジング（Eager/Lazy）
     - ブリッジングの問題をを特定する
     - 時間を測定してブリッジングのコストを測定する

## 414_Understanding Crashes and Crash Logs
Hall 1 — 11:00 AM to 12:00 PM

Sudden app crashes are a source of bad user experience and app review rejections. Learn how crash logs can be analyzed, what information they contain and how to diagnose the causes of crashes, including hard-to-reproduce memory corruptions and multithreading issues.

急なアプリのクラッシュは、ユーザーエクスペリエンスの悪さとアプリレビューの拒否の原因です。 クラッシュログの分析方法、その中の情報、クラッシュの原因を診断する方法（難解なメモリ破損やマルチスレッドの問題など）を学びます。

 - クラッシュとは何か、どのようなときにクラッシュするか
   - CPUがコードを実行できない
   - OSがポリシーを強制
   - 言語が間違いを防ぐ
   - 開発者が間違いを防ぐ
 - クラッシュログにアクセスする
   - Crashes Organizer
   - Open in project
   - クラッシュポイントがハイライトされる
   - スタックトレースを辿って原因を探す
 - Device Window > View Device Logs
 - Symbolication
   - dSYM
 - クラッシュログの分析
   - Show in Finderでクラッシュログの中身を見る
   - 端末情報
   - クラッシュのタイプ、理由
   - クラッシュメッセージ
   - クラッシュしたスレッドのスタックトレース
   - レジスタ状態
   - ロードされたバイナリ情報
 - AssertionとPrecondition
 - OSによるアプリの停止
   - Watchdog events
   - Device overheated
   - メモリの枯渇
   - 不正なコード署名
   - SIGKILL
 - 起動タイムアウトを防ぐ
   - アプリレビューで多いクラッシュ理由
 - メモリエラー
   - 参照カウンタが解放されすぎ
   - オーバーフロー
   - EXC_BAD_ACCESS（SIGSEGV)
   - ivar（インスタンス変数）
   - isa（このオブジェクトがインスタンスであるクラス定義へのポインタ）
   - objcのrelease関数が何をしているか
   - lldbコマンドでクラッシュログを見ていく
     - crashlogコマンド
     - disassembleコマンド
   - クラッシュログからどのクラスのどのプロパティが解放されすぎかまで解析できた
   - よくあるメモリエラーの症状
     - crash in objc_msgSend or retain/release
     - unrecognized selector exception
     - abort() inside malloc/free（freeを二回呼ぶなど）
   - クラッシュ分析Tips
     - クラッシュした行以外のコードを見る
     - クラッシュしたスレッド以外のスレッドスタックトレースを見る
     - クラッシュログをよく見る
     - アドレスサニタイザーやゾンビをメモリエラーの再現に利用する
 - マルチスレッドでの問題
   - 再現や診断が難しい
   - メモリ操作の競合?corruptionがよくある原因
   - マルチスレッドが同じ行を実行
   - Demo
     - 複数のスレッドのスタックトレースを見ると同じ行を実行していることがわかる
     - EXC_BAD_ACCESS
     - スキームエディタでDiagnostic > スレッドサニタイザーを有効化、問題があれば停止させるチェックをon
     - 複数スレッドが同じメモリアドレスにアクセスしていることがわかる
     - スレッドセーフにさせるために、シングルスレッドでCollectionにアクセスさせる
       - Collectionをprivateに
       - DispatchQueueを定義（デフォルトでシングルスレッド）
       - publicなsubscriptを実装（queue.syncで同期的に値を返す、queue.syncで同期的に値を取得）
   - スレッドサニタイザーはシミュレータでのみ動作
   - DispatchQueueのラベルはスタックトレースで表示される

## 415_Behind the Scenes of the Xcode Build Process
Hall 2 — 2:00 PM to 3:00 PM

Ever wonder what happens when you build your project in Xcode? Learn how Xcode automates the steps required to build an application, and go behind the scenes to learn how clang, swiftc, and the linker work together to turn your source code into a working program.

Xcodeであなたのプロジェクトをビルドすると何が起こるのだろうか？ Xcodeがアプリケーションを構築するために必要な手順を自動化する方法を学び、clang、swiftc、およびリンカーが連携してソースコードを作業プログラムに変換する方法を学びましょう。

 - ビルドプロセスは1000以上のタスクからなり、xcodebuildコマンドで実行できる
   - swiftc
   - clang
   - ld（1 つの出力オブジェクト・ファイルに結合して、 外部参照を解決）
   - actool
   - ...
 - ビルドプロセスの実行順
   - 各タスクの依存関係の順
   - リンカのタスクは最後
 - ビルドシステムについて開発者ができること
   - タスクの実行順序について考えるのではなく、タスクの依存関係について考える
   - 依存関係はどこからくる
     - リソースファイルなどの組みこみ
     - ターゲットの依存（Target Dependencies）
     - 暗黙的依存（Link Binary With Libraries）
     - その他ビルドフェーズでの依存
     - Scheme設定
     - InputとOutputの宣言
     - プロジェクトの依存の自動リンクの設定（Link Frameworks Automatically）
 - Clangビルド
   - C, C++, Objc, Objc++のApple公式コンパイラ
   - 結構難しい話。。。
 - Linking
   - 全てのコンパイラの出力を一つのファイルに結合
   - オブジェクトファイル（.o）とライブラリ（..dylib, .tbd, .a）が入力
   - シンボル（コードやデータの断片、他のシンボルへの参照を持つものもある）

## 417_Testing Tips & Tricks
Hall 2 — 3:20 PM to 4:00 PM

Testing is an essential tool to consistently verify your code works correctly, but often your code has dependencies that are out of your control. Discover techniques for making hard-to-test code testable on Apple platforms using XCTest. Learn a variety of tips for writing higher-quality tests that run fast and require less maintenance.

テストは、コードが正しく動作することを一貫して検証するために不可欠なツールですが、多くの場合、コードに依存しないコントロールがあります。 XCTestを使用して、Appleプラットフォームでテスト困難なコードをテスト可能にする技術を発見してください。 高速で実行され、メンテナンスの必要がない高品質のテストを作成するためのさまざまなヒントを学びます。

 - ネットワーク通信リクエストのテスト
   - テストのピラミッド
     - End-to-end
     - Integration
     - Unit
   - APIRequestプトロコルを作成
     - リクエスト処理を抽象化
     - コンストラクタDIで実装を注入できるようにする
 - NotificationCenterを含めたテスト
   - NotificationCenterのインスタンスをコンストラクタDIできるようにする
   - デフォルト引数は.defaultにする
   - テスト時はNotificationCenterのインスタンスを生成する
   - 外部の影響を受けなくなる
 - プロトコルでのモック化
   - サブクラス化でのモックは動作するが、リスキー
   - サブクラス化でのモックはメソッドをoverrideするのを忘れがち
   - プロトコルでモック化しよう
 - テストの実行スピード
   - 人工的な遅延処理は不必要な場合が多い
   - Mockの仕組みで遅延処理をなくそう
   - テスト実行の場合はマクロで判定してテストに関係ない処理を実行しないようにする
