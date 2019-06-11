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
