# 232_Advances in Natural Language Framework

- 内容
  -  テキスト分類
    - 感情分析
      - -1 ~ +1の値で評価
      - NLTagger / tagSchemeを.sentimentScoreにする
      - レビューの内容によってレビューの入力テキストの色をリアルタイムで変化させる
  - ワードタギング
    - 人の名前、場所、名詞など文章の単語にタグ付けする
    - TextCatalog
    - NLGazetter
    - tagSchemeを.nameTypeOrLexicalClassにする
  - Word Embedding
    - Wordをベクター表現にマッピング
    - ベクター空間へのマッピングと同様
    - 写真アプリではこれを使ってあいまい検索可能に（FUzzy Search）
    - OS組み込み（日本語のサポートは現在なし）
    - カスタマイズとして組み込みの情報以外から取得することも可能
      - word2vec/GloVe/fasttext/Custom Neural Network
    - API
      - NLEmbedding（言語を選択）
      - enumerateNeighbors
      - MLWordEmbedding（カスタムWord Embedding）
    - Podcast Embeddings
      - レコメンドシステムのEmbedding
  - テキスト分類のための転移学習
    - アノテーション付き学習データ
    - より小さいアノテーション付き学習データと学習済みモデルを組み合わせる
    - より小さいアノテーション付き学習データとWord Embeddingを組み合わせる
    - どちらを選択するかAPIで指定が可能
    - dynamicEmbeddingはニューラルネットワークを利用する

- 感想
  - 難しいけどう上手く使えばECアプリでもサジェスト、レコメンドなど何かできそう
  - 日本語をどこまでサポートしているのか気になる

- メモ
