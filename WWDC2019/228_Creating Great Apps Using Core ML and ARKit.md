# 228_Creating Great Apps Using Core ML and ARKit

- 内容
  - 機械学習でダイスを認識する
  - Object Detectionでダイスの数を数えるデモ
    - https://developer.apple.com/documentation/vision/vnrecognizedobjectobservation
    - CALayerでBounding Boxの表示
  - ダイスの目を認識する
    - データの収集とアノテーション
    - サイコロが振り終わるのはいつ？
      - モデルのアウトプットを監視する（ラベルとBoundingBoxの重なりを閾値で判定）
  - Inputを処理する
    - PencilKitで手書き文字を書いて、それを入力として認識する
    - 手書き文字を認識して、ダイスの目の合計と同じか判定するゲームのデモ
    - SFSpeechAudioBufferRecognitionRequest()
      - 音声認識もプラス
      - https://developer.apple.com/documentation/speech/sfspeechaudiobufferrecognitionrequest
  - すごろくゲーム
    - ARKitも利用
    - 2つの目をふって+するか-するか選択できる（選択は手書き文字）
    - その数だけ進む

- 感想
  - 思ったよりシンプルなセッションだったけど面白かった
  - コードの話はなくはないが、どちらかというと概念的なセッションだった
  - ARである必要はあったのか謎

- メモ
