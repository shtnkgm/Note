# 237_Building Custom Views with SwiftUI

- 内容
   - 親Viewから子Viewのレイアウト処理の流れ
   - HStackのViewのレイアウト方向はロケールによって自動で変わる
   - Stackがどのようにレイアウトを行うか
   - Viewのレイアウトの優先度
     - .layoutPriority(1)をセット
   - alignment
     - HStackのaligmnentを.bottomにしてもテキストのベースラインはずれる
     - その場合は.bottomよりも.lastTextBaselineが有効
     - Imageだけ下にずらすことも可能
     - VerticalAlignmenのExtensionで縦方向の新しいalignmentを作成できる
   - Drawing
     - Shape、Circle、Capucel、Eclipses
     - グラデーション、AngularGradient
     - Shapeプロトコルでカスタムシェイプを作る
     - ViewModifierプロトコルに準拠してアニメーションTransitionを定義

- 感想
   - Viewのレイアウトの仕組みがわかるセッションなので、レイアウトが上手くいかない時に見直すと良さそう
   - SwiftUIの拡張方法を色々知っておくと、インタラクティブで自由度の高いコーディングができそう

- メモ

# 238_Accessibility in SwiftUI

- 内容
  - SwiftUIでのアクセシビリティ実装について
  - Voice controls
  - Full Keyboard Access
  - アクセシビリティは全ての人のためのもの
  - Label/Value/Trait,Role/Default Action/Custom Action
    - Labelは理解しやすくする
    - ActionはInteractableにする
    - 並び順、グルーピングなどでNavigatableにする 
  - SwiftUIで自動で付与される項目
    - Label/Trait,Role/Default Action
  - Accessibility Notifications
    - 画面の表示情報が変更された時に通知する
    - `@State`プロパティが変更された時に自動で通知
    - 「Toggle Value Changed: 1」
  - Accessible Custom Controles
    - ButtonStyleプロトコルでボタンをカスタマイズ(.ButtonStyleで初期化)
    - Imageにlabelを設定する
    - Pickerにlabelを設定する
  - API
    - .accessibility(label:)
    - .accessibility(addTraits:)
    - .accessibility(value:)
    - .accessibilityAction(named:) { }
    - 色のコントラストを確認するアプリでのデモ
    - .accessibility(visibility:)
  -  Accessibility Tree
    - UIKitとの連携
    - .accessibility(sortPriority: 1)

- 感想
  - ButtonStyleプロトコルとか用意されてるし、デザインシステムの導入もSwiftUIだとやりやすそう
  - 新しいAccessibilityを使ってイメージが湧いてから動画を見直すと良さそう（途中のデモでも少し分かる）
  - 

- メモ

# 614_Metal for Machine Learning

- 内容
 - Metal Performance Shaders
 - 推論グラフ
  - 畳み込み、プーリング、フィルターなど多数の層（Node）を重ねる
    - MPSCNNConvolutionNode
    - MPSCNNLossNode
    - MPSCNNPoolingNode
    - MPSNNFilterNode 
  - Style Transfer
    - Content画像にStyle画像のスタイル適用して新しい画像を生成する
    - Style Loss Networks
    - Content Loss Network
    - Gram Matrix
     - L2 loss
  - Random Number Generation（乱数生成）
    - Generative Adversarial Network（GAN）/ 敵対的生成ネットワーク
      - 教師なし学習
      - 生成ネットワーク（generator）
      - 識別ネットワーク（discriminator）
      - Discriminatorで本物かどうか判定する（Real or Fake）
      - Discriminator Training Network（生成ネットワークに騙されないように学習する）
      - Generator Training Network（識別ネットワークを騙せる画像を生成できるよう学習する）
    - MPSCommandBuffer
    - MPSPredicate 
  - commitAndContinue
  - MLDenoising
    - 入力画像をネットワークに推測させて、損失関数（loss）で評価する
    - MTLCommandBuffer
    - MPSImage
    - 

- 感想
  - 途中から参加したがほとんど内容が理解できなかったが、キーワードを拾って調べる
  - iOSやMacでもニューラルネットワークを用いた機械学習ができるらしいけどどのくらい時間がかかるのか
  - iOSでGAN実装は面白そう

- メモ

# 

- 内容

- 感想

- メモ