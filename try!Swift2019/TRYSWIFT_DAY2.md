# try! Swift 2日目

## 魔法の法則 @davedelong
  - Appleの人
  - Brandon Sanderson
    - お気に入りのファンタジー作家
    - 日本語になっている本もある
    - 面白い本を書くときの法則
  - 十分に高度な技術は魔法と区別が付かない
    - iPhone端末も魔法
  - 魔法の第一法則
    - ユーザーに何が起きているのか理解してもらう必要がある
    - その責任は作者にある
    - 質問を予想する
    - 解決策へのガイド
    - どうやって?（ここでいうユーザーはライブラリの開発者）
      - Swiftの型システムを利用する
      - 規則に従って慣れ親しんだパターンを使う
      - ヘルプやエラーメッセージ
      - ドキュメントとユニットテストが完全であること
    - fatalErrorで知らせる（実行時エラーまでわからない）
    - @available でコンパイル時にもエラーで知らせる
      - コンパイラによる自動Fixで開発者を教育
      - ドキュメントで案内
  - 魔法の第二法則
    - 制限は権力よりも重要
    - できないことはできることよりおもしろいことが多い
      - 物語での登場人物の制約（できないこと）
        - スーパーマンの弱点
      - 制約は創造的であることを強制する
    - 時間、チーム、個人の能力
      - 制約を元に我々は行動する
      - 創造性を発揮して制約を乗り越える
      - 制約によって本来考えなかった選択肢が登場する
  - 魔法の第三法則
    - 新しいものを使う前に既に持っているものを拡張する
    - 隠された深さを探すことはエキサイティング
    - 他の人が見つけていないものを見つけられる
    - 一見単純であり、しかも奥深い
    - コードのリファクタリングもその一つ
    - 検討していないユースケースは?
    - サポートされていない機能は?  

## ポートレートモードを自作しよう @koooootake
https://speakerdeck.com/koooootake/making-portrait-mode-yourself
  - ポケモンマスター
  - DeNAマンガボックスの開発
  - iOSのカメラアプリのポートレートモードで背景ぼかせる
    - 深度情報（Depth）を使っている
  - Depthがないときは?
    - 2次元画像を映えさせたい
    - 被写体と背景の分離をDepthを使わずにする
      - CoreMLではうまくいかなかった
      - キャラクラー毎に学習が必要
    - グラブカット?とリタッチで
    - あとは背景をガウシアンブラーでぼかす
    - 被写体の縁がぼかした時に背景にあふれるので被写体を消す
    - 被写界深度も調整できるようにした
  - Demoアプリ
    - https://github.com/koooootake/Portrait-without-Depth-ios

## Swiftでソーシャルネットワークをつくろう @dokun24
  - 二人で発表
    - Ian: IBMのテクニカルリード、Swiftコミッター、Kitura（キトラ）の開発
    - David: モバイル開発者、IBMデベロッパーアドボケイト
  - モバイルバックエンド
    - Standalone
    - MBaaS
    - Bespoke（サーバーサイドSwift）
  - Microservices
    - コンパイル済みバイナリなので起動が早い
    - Javaなどよりメモリ使用量が少ない（コスト削減になる）
    - 相互互換性
  - 一例
    - Allegro
  - docker/HELM/kubernetes
  - OPENAPIは何してくれるか
    - Kituraが自動生成したAPIドキュメント
    - OPENAPIのエコシステムが強み
    - Swift Server Working Group（SSWG）
    - Language Server Protocol（LSP）
  - 本を書いたよ「Server Side Siwft with Kitura」
  - Demo
    - EmojiJournal
    - Xcodeを利用せずにアプリをビルドする
    - シミュレーターで実行
    - VSCodeでLSPを利用したコーディング、自動コード補完
    - OPENAPIのAPIドキュメントを見る
    - OPENAPIUI
    - サーバーのデバッグが簡単にできる
    - WebSocket技術を利用、アプリとブラウザでリアルタイムに更新される
  - 本番系で使えるの？
    - onlineswiftplayground.runでKituraが使われている
      - http://onlineswiftplayground.run/
    - www.agenda.comもKitura
      - https://www.agenda.com/
    - ドイツのIoTバンキング
      - https://bankingofthings.io/
    - CPU/RAMの消費量も悪くないというグラフ
  - http://ibm.biz/trykitura

## 休憩

## Swift Hardware Hacking @mostgood
  - Geany（IDE、Swiftは非対応）
  - v2ではユーザー認証とコンセント電源に対応
  - 回路についてのお話
    - ラズベリーパイ
    - GPIO(General-purpose input/output)
    - SwiftyGPIOというライブラリを使う
      - https://github.com/uraimo/SwiftyGPIO
    - Relayはスイッチ
    - デジタル信号、電圧でオンオフ、1 = 3.3v / 0 = 0v
    - アナログ信号
    - MCP3008（8チャネルのA-Dコンバータ）
  - 光の量で開いてるかしまっているかを検知 
  - 荷重センサーで金額を計算する（抵抗値の変化）
    - HX711
    - アナログ信号は0/1だけではない
    - アナログ信号をどうデジタル信号にするか
      - バイナリ
      - 12bitなど情報の長さを決めておく
        - 24bitなら24回ループして1bitずつ読み込む
  - Bluetooth（BLE）
    - Central（iOS）とPeripheral（ラズパイ）
    - GATT Profile
      - https://www.bluetooth.com/ja-jp/specifications/gatt/generic-attributes-overview
    - CoreBluetooth
  - 全体構成

## SwiftSyntax で便利を実現する基礎 @orga_chem
https://speakerdeck.com/orgachem/how-to-use-swiftsyntax-for-better-productivity-japanese-version
  - SwiftSyntaxで静的検査やコード生成ができる
    - https://github.com/apple/swift-syntax
  - コードを読み書きしやすいデータにする
    - if文は条件と複文からなる
    - Optional束縛条件
    - 木構造
    - 構文木
    - オレオレSwiftLintが作れる
  - コード生成
    - SwiftSyntaxのRenameRewriterクラスで書き換え
  - これ面白そう！

## Swift type metadata @kateinoigakukun
  - Swiftの型のメタデータについて
  - 静的型付けだが、実はランタイムで動的な部分がある
    - 例えばクラス名の取得部分
  - 型.Type型の情報（型.selfで取得）
    - CustomStringConvertibleには準拠してないはず
  - オープンソースなのでソースコードをみてみる
    - SwiftCore
    - SwiftRuntime
    - @_silgen_name リンク時につけられる関数の名前
    - メタデータに含まれる型名を取り出す関数
    - Metadata > Nominal Type descriptor > Type Name
    - SwiftコードでMetadataを実装してみる
      - Relativeポインタ（参照先アドレスへのオフセット）
      - サブタイプ関係がないのでunsafeBitCastを使う
  - メタデータのユースケース
    - インスタンスのアロケート
    - ダイナミックメソッドディスパッチ
    - リフレクション
  - Method Swizzling（ObjC黒魔術）
    - クラスのメソッドはVTableという関数ポインタで取得
    - 関数ポインタを入れ替える
  - OSSでのMetadataを利用した事例
    - https://github.com/Zewo/Reflection
    - https://github.com/wickwirew/Runtime
    - https://github.com/alibaba/HandyJSON
    - https://github.com/kateinoigakukun/StubKit
      - 引数なしで任意のインスタンスを生成
  - 注意
    - Siwft4.2ではABIの安定性なし（メタデータの構造が変わる）
    - Swift5で安定性が確立
    - SwizzlingはSwiftの型の最適化で元に戻ってしまうことがある
    - 大いなる力には大いなる責任が伴う

## モバイルのデザインシステムを構築する @krstnfx
https://speakerdeck.com/krstnfx/building-a-mobile-design-system
  - デザインシステムとは
    - 一連のコンポーネントを再利用するための仕組み
    - レゴブロック
  - どうやったら個々のコンポーネントに分解できるのか
    - Atomic Web Designのブログ
  - 誰のため?
    - デザイナー、エンジニア、ユーザー
    - デザインの時間を減らす
    - 開発時間を減らす、コードの再利用
    - 同じような振る舞いで早い時間で理解できる
  - どのようなアプリに向いてる?
    - 反復するデザイン、ブランドの統一 
    - Airbnb
      - https://airbnb.design/building-a-visual-language/
    - Lyft
  - オススメの記事
    - https://medium.freecodecamp.org/how-to-build-a-design-system-with-a-small-team-53a3276d44ac
  - フォントと色
    - コードでカスタムフォント、カラーを定義するところから
    - タイポグラフィシステム
      - enumで列挙
    - ColorAsset
      - enumかAssetフォルダで名前をつける
      - 私のチームではハイブリッド型
  - UI controllers
    - UISwitch
    - 独自クラス（ブランドスタイルに合わせて色や形状が違うもの）
  - UI Components
    - APIデザインも重要、どんなエンジニアでも使えるように
    - アプリ内での一貫性
    - enumのstyleを切り替える
  - View Components
    - TableViewのセル
    - テキストフィールド
    - デザインシステムの構築は企業やチームに特化すべき
  - 最後に組み合わせる
    - https://github.com/airbnb/epoxy
    - これはまだAndroid用(Kotlin)  
  - デザインシステムを作るとき
    - Documentationをつくる
      - Googleのマテリアルデザインは包括的なドキュメントになっている
    - エンジニアとデザイナーがうまくコミュニケーションを取る
    - オーバーエンジニアリングはダメ
      - 必ずしも作らなくてもいい

## ランチ

## Swiftにおける音の成形 @b3ll
  - シンセサイザー
    - Roland Juno-60
    - Prophet-5
    - プレステの起動音（Roland D-50）
  - どんな仕組み?
    - オシレーター（波をつくるもの）
      - アンプリチュード（音の大きさ）
      - 周波数（Hz、波の数、音程）
      - 波形（三角、矩形、sawtooth...）
         - 矩形は01なので説明しやすい
         - コンピューターっぽい音
    - エンベロープ
  - CoreAudio
    - 音作って出すまでやることがたくさん
  - AudioKit
    - https://github.com/AudioKit/AudioKit
    - パルス幅の変更
    - ADSR（アタック、ディケイ、サステイン、リリース）
      - 音量がどう変化するか
      - 音の立ち上がり、減衰、持続、フェードアウトのこと
      - 同じ音でも聞こえ方が変わってくる
    - Effect、音自体を変える
      - フィルター
        - ローパスフィルター
          - 高周波を取り除く
        - ハイパスフィルター
          - 低周波を取り除く
        - ノッチフィルター
          - 中間音だけを通す
        - レゾナンス（共鳴）
          - 遮断周波数付近の音を強調
      - Delay
        - エコー
      - Chorus
        - 同じ信号を二つのDelayで
        - 音の幅
      - Reverb、残響
  - アーティストになって人と共鳴できるようなものをつくろう

## iOS端末を利用した心理学研究の背景と展望 @expensive_man
  - VALUのiOSエンジニア
  - 心理学
    - 刺激に対する反応を観察してその相関関係を調べる
    - 反応までの時間
    - 反応の頻度
    - マルチタッチスクリーン
  - 動物としてみた人
  - 現実の人
    - スマホは朝から晩まで使っている
    - 多数のセンサーで反応を計測できる
    - タップ操作
    - ぐるっと回す操作
    - スワイプ角度
  - 楽しい操作とかをエンジニア間などよりオープンなコミュニティで発展させたい 

## SwiftCheckで始めるProperty-based Testing @tobi462
  - DeNAのSWETエンジニア
    - 自己紹介まで英語でチャレンジ
    - Pengin-mura
  - Property-based Testingとは
    - 性質を定義
    - ランダム値でテスト
  - Example-based Testing（普通のテスト）
    - 具体的な入出力で検証
    - 検証パターンはどのくらい必要?
      - 現実的には入力値は無限、どうやって選ぶ?
      - 境界値分割、同値分割
  - Property-based Testingでは性質に着目
    - reversed
      - 反転してもサイズは変わらない
      - 2回適用すると元に戻る
      - これはどんな配列でも満たす性質
  - ランダムな配列を生成し、先ほどの性質を満たすか検証
  - SwiftCheck
    - https://github.com/typelift/SwiftCheck
    - property関数
    - forAll関数（Boolを返すクロージャ）
    - Arbitrary
      - ランダム値を生成するプロトコル
      - プリミティブ型のarbitraryプロパティから独自型も準拠できる
    - Shrinking
      - Arbitraryのshurink関数
      - テストに失敗したらより小さな値でテスト
      - 最小の失敗ケースがレポートされる
      - 原因調査が楽になる
  - ユースケース
    - ランダム性のあるアルゴリズムに対するテスト
      - 迷路の生成
        - 性質: 迷路はいつもゴールにたどり着けるべき
    - 対象性のあるアルゴリズムに対するテスト
      - エンコードとデコード
    - 高速なアルゴリズムと低速なアルゴリズム
      - 一般的に高速なアルゴリズムは複雑
      - しかし、両者の結果は同じはず
      - 高速なアルゴリズムの検証に低速なアルゴリズムの結果を利用する

## All about linking libraries @k_katsumi
  - リンクの問題は様々
  - 動的リンクと静的リンク
    - リンクのタイミング
    - バンドルの有無
  - フレームワークはmodule.modulemapを持てる
  - ライブラリにはバンドルがない
  - ブリッジングヘッダ
  - Module Map
  - リンクに関しての中身
  - Header Search Path
  - TODO: 追いつけなかったけどすごく良さそうな資料なのであとで資料読む

## 賢者のString @Ilseman
  - Appleのエンジニア
  - Swift Standard Libraries
  - 日本語で自己紹介
  - Stringとは何か
    - いろんなひとにどんな風に使っているのか聞いた
    - 「一次元のオブジェクトで時空を超えるもの」
    - Unicodeを意味あるものにする
  - Stringの哲学
  - なんで難しいのか
    - Unicodeは互換性があるのがいいところ
    - Stringは複雑性を加えてしまっている
  - Characterの集合
  - よいデフォルト
  - Graphemes（言葉を表すために使われる書かれた記号）
    - Graphemesの有無で文字数が変わってきてしまう
  - 文字の順序は国によって異なる、コンテキストによっても変わる
  - マシンが行う順序付け
    - 場所やコンテキストによらず一貫している必要がある
    - 数学的な利点が必要
    - 高速
  - Stringの進化の歴史
    - Swift3 -> Swift5
  - 今後のはなし
  - オツカレサマデス
  - ...endIndex

> 結構疲れた
> おれはメモをやめるぞ！ジョジョーーッ！！

## 休憩

## アセンブリ、君ならできる！ @armadsen

## Swiftコンパイラにコントリビュートする @kitasuke

## Core Dataを守るために @DonnyWals

## 次へつなごう— Extending a hand to the next generation of Apple developers @hellomayuko

## Party
