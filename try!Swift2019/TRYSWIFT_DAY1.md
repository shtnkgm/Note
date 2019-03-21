try! Swift 1日目

# native macOS application、またはAppKitの世界 @1024jp
  - MacOSアプリの開発について
  - ネイティブに振る舞うことはiOSよりも重要
    - ユーザーが物理的なWindowを意識する
    - 同じディスプレイ上で他のアプリケーションと同時に表示される
    - MacOSの部品として統一感のあるデザインする必要がある
  - Titlebarの話
  - アプリを利用していることを意識させないことが理想
    - 開発者のエゴを殺し、ユーザーには目的に集中させる
  - Marzipanはただのエミュレーターなのでおすすめしない
    - ネイティブフレームワークを使い、OS毎のデザインガイドラインを読むべき
    
# 脱Swiftリテラル初心者 @___freddi___
  - 42の数字がコンパイラに解釈されるまで
    - リテラルプロトコル
    - CGFloatは環境によってtyepaliaseを分岐（Float/Double）
    - コンパイラ組み込みプロトコル（CaseIterbleもそのうちのひとつ） 

# アクセシビリティのためのカラーコントラスト @emarley
  - ユーザーがどうやってユーザーがメッセージを理解するのか
    - テキスト色をどこまで明るくしてもいいのかどうやって知るか
    - 止まれと言う標識は文字が読めなくても赤い色でわかる
    - 文字色と背景色のコントラスト比率
      - HIGに専門家がデザイン原則をまとめている、コントラスト比率が書いてある
      - HIGにはないが、Web Content Accesibility Guidelineに根拠が書いてある
      - 7:1以上が読みやすい（最低でも4.5:1）
      - Webサイトでチェックしよう https://webaim.org/resources/contrastchecker/
      - 数学の方程式になっているのでSwiftコードでプロセスを説明する
        - 色空間の変換
        - RGB分解
        - 二次曲線から線形曲線に
        - 人間の目の補正をかける（緑は明るく見え、青は暗く見える）
        - 最後に輝度計算をしてそのコントラスト比率を出す
  - Dark Mode
    - そろそろiOSのDark Modeでるのではないか
    - UIColorのdarkTextやlightTextのようなプロパティはライトモード前提なので見直されるかも
    - ColorAsset設定が拡大されるはず
  - すべての人へのアクセシビリティ
    - 明るいところでも暗いところでも

# 休憩    

# Swift Light @bugKrusha
  - 3Dレーザープリンタ
    - SVGのデザインからSwiftコースターをつくる
    - アプリでデザインを変更できる
  - 開発しているアプリの作りの話
    - ピクセルグリッドからベジエ曲線をつくる
    - ドラッグするグループのレイヤー
    - CALayerの扱い
    - CGAffineTransform（アフィン変換）
    - iOSとSVGで回転ポイントが異なる（iOSは中心、SVGは左上）
  - アプリの安全性を担保する
    - バグでプリントする素材を壊してしまうのが最悪
    - 値型
    - 抽象化
      - 小さい責務ごとに独立した型をつくる
    - テスト
      - テストがされていないコードは不完全なコード
      - 統合テストももちろんやる
    
# 限定的なimportの明示とその効果 @noppefoxwolf
  - import文のオプションの話
  - attributes
    - `@testable`（）
    - `@_exported`（プライベートなので非推奨）
  - submodule
  - importKind
    - classやstructを指定した場合の注意
    - overrode関数は個別にimportできない
    - 別モジュールでの同じ名前メソッドの衝突に問題なければ使わなくて良い
    - ビルド時間に効果はなし
    - バイナリサイズにも効果なし

# protocol/extensionにジェネリクスを入れたい @_yyu_
  - タプルとリスト
    - Anyのリストは取り出した時にキャストが必要で微妙
    - ヘテロジーニアスリストをつくる（HList）
    - 各要素の型が保持され、配列に複数の型を持てる
  - appendの実装をする
    - 型が複数あるので簡単ではない
    - プロトコルエクステンションを使う
    - 型に実装を追加することができる
    - オーバーロードの機能に近い（型で機能が決まる）
    - プロトコルエクステンションをオーバーロードで模倣できるのか、いやむしろより高機能
    - 型でコンパイル時に機能をディスパッチする
    - HAppend、HNilプロトコルをつくる
  - 作ったけどSwiftの型推論が追いつかない、プロダクションコードとしては難あり

# KeyPath入門 @terhechte
  - KeyPath<Root, Value>
  - KeyPathでプロパティへのリンクをつくる
    - 参照したり変更できる
  - KeyPathはネストもできる
  - 書き込みはWritableKeyPath<Root, Value> 
  - RefarenceWritableKeyPath<Root, Value>もある（紹介のみ）
  - PartialKeyPath
  - AnyKeyPath（型消去）
    - 同じArrayに入れることができる
    - 正しいKeyPathに戻すことも可能
  - KeyPathの組み合わせ
    - ランタイムでKeyPathを合わせていく
  - 一般的なアプリでの設定の抽象化の話
    - プロファイルの設定とプライバシー設定
    - タイトルやサブタイトルなどメタ情報もある
    - KeyPathをプロパティとして保持
  - KeyPathのTips
    - 型消去するものを選ぶ
    - KeyPathの型は戻せる
    - Hashableに準拠しているので辞書キーに使える
  - KeyPathのライブラリもある
    - Kuery、CoreDataで文字列クエリを避けられる
    - KeyPathKit、複数の条件でソートする場合に有用

# ランチ

# テストケースでMemory Leakを発見する @tarunon
  - iOSにはガーベジコレクションはない
    - 参照カウントでメモリ管理を行う
    - リファレンスがなくなった時にオブジェクトを解放する
  - どうやって防ぐか
    - コードレビュー
    - コーディングルール
    - Lint
    - Memory Graph Debugger
  - テストケースで防ぐ
    - Mirrorwを利用する
      - オブジェクトが持っている全てのプロパティを取得できる
      - トップのオブジェクトを解放したらすべて解放されるはず
      - weak変数にいれてnilになるかチェック
    - XCTAssertNoLeakをつくった
      - https://github.com/tarunon/XCTAssertNoLeak
      - 循環参照が起きる参照型とそうでない値型を分ける
      - mirror.displayStyle
      - mirror.children

# PixarのようなグラフィックをSwiftで実現する

# ARKitのアプリを作ろう

# Introducing SourceKit-LSP

# Swift Server Update

# 休憩

# SwiftのアプリでCやC++、Objective-Cのフレームワークを使おう

# MachObfuscator

# Siri ShortcutsとNSUserActivityによるエンゲージメント推進

# try Prototype!

