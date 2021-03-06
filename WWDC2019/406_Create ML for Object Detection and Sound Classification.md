# 406_Create ML for Object Detection and Sound Classification

 - 内容
    - CreateMLでオブジェクト検知と音声分類をする話
    - オブジェクト検知
      - 画像分類は有名、さらに画像内の複数のオブジェクトを検知したい
      - 学習データに画像内の位置情報やラベルなどのアノテーション情報をJSON形式の1ファイルで付与する
      - 複数のサイコロの目を判定するモデルを作るデモ
      - Outputタブでモデルの推論結果を確認できる
      - iPhoneを接続してカメラで撮影した結果を判定することも可能
      - さらに違うサイズ、色、数字のサイコロに対応する
      - ???
      - 学習データは1つのクラスにつき30毎以上の画像推奨、複数の角度、複数の背景、異なるライティング環境が良い
    - 音声分類
      - 異なる音源を判定したり、同じ音源でも区別することができる（赤ちゃんが笑っているのか泣いているのかなど）
      - 話し声や拍手、楽器の音を判別するモデルを作るデモ
      - Outputタブではマイク入力からテストができる
      - ノイズも学習データに含めると良い
      - 1ファイルに複数の音声を含めることは推奨しない、判別クラス毎にファイルを分ける
      - Sound Analysis Frameworkで学習モデルをiOSで利用できる
      - timeRangeが取得できる

 - 感想
    - アノテーション情報はどうやってつくる？
    - アノテーション情報のJSON形式は何か決まりがある？
    - グラフのlossの値が変化していく意味がわからなかった
    - 学習の状況がグラフで見れるのは面白いしわかりやすい
    - ValidationとTestingはどう違う?
    - 音声分類面白そう
    - サポートしている音声ファイル形式は?
    - 声から人の判別とかできるかも、鳥とか動物の鳴き声もできる？
    - Sound Analysis FrameworkのAPIはVision FrameworkのAPIにとても似ているのでVision使ったことがあればすぐに使えそう

 - メモ
    - 最初のデモの最後を見逃したのであとでみる
    - Sound Analysis Frameworkをチェックする
    - https://developer.apple.com/documentation/soundanalysis
    - SNResultsObserving
