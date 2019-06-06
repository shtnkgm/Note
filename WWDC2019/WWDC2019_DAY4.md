# 226_Data Flow Through SwiftUI 

- 内容
  - DataFlowの原則
    - データとは何か
    - Dependencyとしてのデータアクセス
    - Source of Truth（マスターとなるデータソースは?）
      - 重複するデータソースはNG
      - 複数のViewで利用するデータは親のViewに持たせる
      - Viewはstructなのでvarでもプロパティの変更はできない
      - Property Wrapperの`@State`を利用する（privateをつけるのを推奨）
  - Updateの仕組み
    - 全ての@StateはSource of Truth
    - Viewはstateのfunction、イベントのシーケンスではない
    - User -> Action -> State -> View -> User ...
    - `@Binding`
      - owenershipなしでread/write
    - ViewControllerはもう必要ない   
  - データを理解する
  - 外部データを利用する
    - Combine Publisher
    - BindableObject Protocol
      - var didChange = PassthroungSubject<Void, Never>()
      - didChange.send() // サブスクライバに変更を通知する
      - `@objectBinding`のDependencyをViewに作る
      - 自動でDependencyのトラッキングをし、同期は不要になる
    - 間接的にDependencyをつくる
      - Property Wrapperの`@EnvironmentObject`を利用する
      - 観察的に参照できるので、Dependency Injectionは不要
      - アクセントカラー、文字の方向、Dark Mode、などなど色々用途はある
    - Source of Truthとなる`@State`とBindableObjectの違い
    - `@Binding`のプロパティにアクセスするには$が必要
    - Stateを効果的に利用できるケース
    - Source of Truthは最小にする
- 感想
  - SwiftUIのデータに関する、求めていた内容のセッション
  - いまいち理解が深まらなかったので動画をもう一度見たい

- メモ

# 228_Creating Great Apps Using Core ML and ARKit

- 内容
  - 機械学習でダイスを認識する
  - Object Detectionでダイスの数を数えるデモ
    - https://developer.apple.com/documentation/vision/vnrecognizedobjectobservation
    - CALayerでBounding Boxの表示
  - ダイスの目を認識する
    - データの収集とアノテーション
    - サイコロが振り終わるのはいつ？
      - モデルのアウトプットを監視する（ラベルとBoundingBoxの重なりを閾値で判定）
  - Inputを処理する
    - PencilKitで手書き文字を書いて、それを入力として認識する
    - 手書き文字を認識して、ダイスの目の合計と同じか判定するゲームのデモ
    - SFSpeechAudioBufferRecognitionRequest()
      - 音声認識もプラス
      - https://developer.apple.com/documentation/speech/sfspeechaudiobufferrecognitionrequest
  - すごろくゲーム
    - ARKitも利用
    - 2つの目をふって+するか-するか選択できる（選択は手書き文字）
    - その数だけ進む

- 感想
  - 思ったよりシンプルなセッションだったけど面白かった
  - コードの話はなくはないが、どちらかというと概念的なセッションだった
  - ARである必要はあったのか謎

- メモ

# 609_Building AR Experiences with Reality Composer

- 内容
  - Reality Composer
    - ARコンテンツを作成するためのアプリ 
  - シーンを組み立てる
    - シーンを選択
    - ビルトインのコンポーネントライブラリからARコンテンツを選択
    - Behaviorsでインタラクションを設定
    - オブジェクトの大きさや位置、形、表面のデザインを設定
    - カメラ位置、角度を変更
  - Behavior
    - Trigger
      - Start
      - Tap
      - Proximity
      - Collision
      - Notification
    - Action Sequence
      - group
      - loop
      - exclusive
    - Actionの種類（表示、回転、強調、移動、カメラを見る、音を鳴らす等）
    - Materialの種類
    - Force
    - Collisionsの種類
  - ProjectとReality Fileについて
    - Reality FileはXcodeで自動でコード生成される
    - ARエンティティにプロパティでアクセスできる
  - Notify Action
  - Notification Trigger

- 感想
  - ARコンテンツをアプリで作れるだけでも面白そう
  - アプリ内でプレビューもできるので、ARとしてどう見えるか確認しやすい
  
- メモ

# 407_Create ML for Activity, Text, and Recommendations

- 内容
  - テキスト分類
    - 感情分析
    - スパム
    - トピック
  - テキスト分類の転移学習デモ
    - ディレクトリ名のラベルは絵文字でもOK
    - 転移学習は時間がかかる（5分はかからない？）
    - Outputに入力すると、入力中でもリアルタイムで判定される
  - 転移学習とは?
    - 学習済みモデルを利用する
    - 昨年の画像分類だけでなくテキスト分類でも可能に
    - セマンティックな文章解析が可能
  - Tips
    - ユースケースにあったアルゴリズムを選ぶこと
      - Advances in Natural Language Frameworkのセッションで説明
    - クラスのバランス
    - データの一貫性（文章の長さなど）
  - アクティビティ分類
    - Jogging/Standing/Gesture/Gaming/Golf/Swimming...
    - Apple Watchでのフリスビーのモーション分類のデモ
    - CoreMotionのデータを利用
    - 1.1MBのモデルサイズしかない
  - モデルの学習方法
    - CSVデータから学習
    - Prediction Window Size（モーションの長さによって決める）
    - PrecisionとRecallの値からさらに学習すべきか判断する
    - Output
  - Recommender
    - これを買い忘れてませんか？の候補を出す
    - レシピと食材
    - Trail / Rating
    - カラムの種類: Group / Item / Rating
    - ハイキングに行った場所と評価を入力するアプリのデモ
    - Itemの関連性を学び、関連性グラフを構築する
    - CSVかJSONファイルから学習する
    - データがセキュアであることを保証する必要がある
    - ラボは金曜2時~

- 感想
  - テキスト分類はすぐ使えそう
  - アクティビティ分類の場合のデータの集め方がわからなかった
  - Reccomenderは学習の仕方のイメージがつかなかったのでまずは触ってみる

- メモ

# 232_Advances in Natural Language Framework

- 内容
  -  テキスト分類
    - 感情分析
      - -1 ~ +1の値で評価
      - NLTagger / tagSchemeを.sentimentScoreにする
      - レビューの内容によってレビューの入力テキストの色をリアルタイムで変化させる 
  - ワードタギング
    - 人の名前、場所、名詞など文章の単語にタグ付けする
    - TextCatalog
    - NLGazetter
    - tagSchemeを.nameTypeOrLexicalClassにする
  - Word Embedding 
    - Wordをベクター表現にマッピング
    - ベクター空間へのマッピングと同様
    - 写真アプリではこれを使ってあいまい検索可能に（FUzzy Search）
    - OS組み込み（日本語のサポートは現在なし）
    - カスタマイズとして組み込みの情報以外から取得することも可能
      - word2vec/GloVe/fasttext/Custom Neural Network
    - API
      - NLEmbedding（言語を選択）
      - enumerateNeighbors
      - MLWordEmbedding（カスタムWord Embedding）
    - Podcast Embeddings
      - レコメンドシステムのEmbedding
  - テキスト分類のための転移学習
    - アノテーション付き学習データ
    - より小さいアノテーション付き学習データと学習済みモデルを組み合わせる
    - より小さいアノテーション付き学習データとWord Embeddingを組み合わせる
    - どちらを選択するかAPIで指定が可能
    - dynamicEmbeddingはニューラルネットワークを利用する

- 感想
  - 

- メモ

# 

- 内容

- 感想

- メモ