# WWDC Run

# 406_Create ML for Object Detection and Sound Classification

 - 要約
    - CreateMLでオブジェクト検知と音声分類をする話
    - オブジェクト検知
      - 画像分類は有名、さらに画像内の複数のオブジェクトを検知したい
      - 学習データに画像内の位置情報やラベルなどのアノテーション情報をJSON形式の1ファイルで付与する
      - 複数のサイコロの目を判定するモデルを作るデモ
      - Outputタブでモデルの推論結果を確認できる
      - iPhoneを接続してカメラで撮影した結果を判定することも可能
      - さらに違うサイズ、色、数字のサイコロに対応する
      - ???
      - 学習データは1つのクラスにつき30毎以上の画像推奨、複数の角度、複数の背景、異なるライティング環境が良い
    - 音声分類
      - 異なる音源を判定したり、同じ音源でも区別することができる（赤ちゃんが笑っているのか泣いているのかなど）
      - 話し声や拍手、楽器の音を判別するモデルを作るデモ
      - Outputタブではマイク入力からテストができる
      - ノイズも学習データに含めると良い
      - 1ファイルに複数の音声を含めることは推奨しない、判別クラス毎にファイルを分ける
      - Sound Analysis Frameworkで学習モデルをiOSで利用できる
      - timeRangeが取得できる
 
 - 感想
    - アノテーション情報はどうやってつくる？
    - アノテーション情報のJSON形式は何か決まりがある？
    - グラフのlossの値が変化していく意味がわからなかった
    - 学習の状況がグラフで見れるのは面白いしわかりやすい
    - ValidationとTestingはどう違う?
    - 音声分類面白そう
    - サポートしている音声ファイル形式は?
    - 声から人の判別とかできるかも、鳥とか動物の鳴き声もできる？
    - Sound Analysis FrameworkのAPIはVision FrameworkのAPIにとても似ているのでVision使ったことがあればすぐに使えそう
 
 - メモ
    - 最初のデモの最後を見逃したのであとでみる
    - Sound Analysis Frameworkをチェックする
    - https://developer.apple.com/documentation/soundanalysis
    - SNResultsObserving

# 222_Understanding Images in Vision Framework

- 要約
  - 人の目を引くもの（顔や目、コントラスト、水平、ライトなど）とオブジェクトセグメンテーションのSaliencyがある
  - Heatmap情報は実はとても小さなCVPixelBuffer
  - Bounding BoxやHeatmapをVision Frameworkで取得できる
  - ユースケースとしてはオブジェクト範囲以外にBlurをかける、オブジェクトの範囲だけCropなど
  - 他のAPIと組み合わせてオブジェクト範囲から画像分類を行うことも可能
  - イラストの類似度を判定するゲームのデモ
  - Face Landmarkの特徴点の数が増えた（65→76）
  - 瞳孔の検知
  - RequestクラスのrevisionプロパティでAPIバージョンをセットする
  - FaceCaptureQualityで顔の撮影クオリティがfloatで取得できる（相対値なので絶対値としての閾値と比較してはいけない）
  - 新しいDetectorとしてHuman、Cats、Dogが追加された
  - Objectトラッキングの精度が向上（木陰に人が隠れてもすぐに追従を再開する）
  - CoreMLを導入する新しいAPI
  
- 感想
  - 画像判別とSaliencyの関連がわかった
  - 後半のTaxonomyとRecallの話がよく理解できず

- メモ
  - Taxonomy（分類学）
  - PrecisionとRecall（PR曲線）
  - デモはサンプルコードがあるのでチェック 

# 215_Advances in Collection View Layout

- 要約

- 感想

- メモ

# 220_Advances in UI Data Sources

- 要約

- 感想

- メモ

# 408_Adopting Swift Packages in Xcode

- 要約

- 感想

- メモ