# 222_Understanding Images in Vision Framework

- 内容
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
