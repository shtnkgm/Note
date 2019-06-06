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
  - 
  
- メモ

# 

- 内容

- 感想

- メモ

# 

- 内容

- 感想

- メモ

# 

- 内容

- 感想

- メモ