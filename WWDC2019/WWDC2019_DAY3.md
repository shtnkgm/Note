# WWDC Run

# 406_Create ML for Object Detection and Sound Classification

 - 内容
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

# 216_SwiftUI Essentials

- 内容
  - Bindingの構文(@State）、詳しくはDataFLowのセッションで
  - 1つの目的のViewを小さく作って大きなViewをCompositionでつくる
  - .font（.subheadline）などのModifier関数は全てsome Viewを返す仕組み
  - Form {}やSection {} でくくるとセクションありのTableViewっぽくなる
  - Controlは環境に適応して見た目が変化するように作られているので、見た目ではなく目的を記述する
  - Voice Overにも自動で対応している
  - Picker
  - https://developer.apple.com/documentation/swiftui/picker
  - FormとPickerの組み合わせ
  - accentColorやdisableなど共通の設定を親のViewに指定することで一括設定できる
  - Environmentは下のViewに継承される
  - saturation
  

- 感想
  - Viewを小さく分割することはパフォーマンスにも影響する?
  - 見た目でなく目的で実装しているのiOS、TVOS、MacOS、WatchOSなど各OSで最適化されたデザインになっているのがすごい
  - 再利用が効くのでOS展開の敷居が低くなった

- メモ
  - VStack、HStackのTrailing Closureは@ViewBuilderアノテーションが付いている
  - ViewBuilder自体はstruct
  - https://developer.apple.com/documentation/swiftui/viewbuilder
  - Viewプロトコル
  - https://developer.apple.com/documentation/swiftui/view
  - State structは@propertyDelegateが指定されている
  - https://developer.apple.com/documentation/swiftui/state

# 220_Advances in UI Data Sources

- 内容
  - セルの差分更新を行った時に整合性が合わない時のクラッシュ問題を解消する新しいアプローチ
  - Diffable Data Source
  - 自動でアニメーションもつけられる
  - insertItems()、performBatchUpdates()の代わりにapply()を実行する
  - UICollectionViewDiffableDataSource / UITableViewDiffableDataSource
  - NSDiffableDataSourceSnapshot
  - データ型はHashableプロトコルに準拠
  - apply()のみを利用すること、insertItems()、performBatchUpdates()は利用しない
  - insertItems / moveItems / appendItems /  appendSectionsでデータソースを更新する
  - パフォーマンスも高速
  - applyはバックグラウンドキューで実行しても安全
  - これがベストなAPI！！
  - iOS13のシェアシートの内部実装でも利用している

- 感想
  - SwiftUIが発表された中、UIKitのセッションだが実用的な内容でプロダクトにも反映できそう
  - アニメーションが自動なのも良い

- メモ
  - https://developer.apple.com/documentation/uikit/views_and_controls/collection_views/using_collection_view_compositional_layouts_and_diffable_data_sources?changes=latest_minor
  - https://developer.apple.com/documentation/uikit/uicollectionviewdiffabledatasource
  - https://developer.apple.com/documentation/uikit/uitableviewdiffabledatasource 

# 408_Adopting Swift Packages in Xcode

- 内容
  - Xcode11からSPMに直接アクセスできるように
  - SPMでパッケージを導入するデモ
  - プロジェクトファイルとxcshareddata > swiftpmに差分が出るのでgitでバージョン管理できる
  - SPMパッケージの構成ファイルの説明（manifestファイル、Sources、Tests）
  - Swift5からのPackageDescriptionをimportしてマニフェストをswiftで記述する
  - 依存関係の解決方法の詳細
    - バージョン番号の付け方→Semantic Versioningに応じてどのようにバージョン管理をするか
      - up to next major / 次のメジャーバージョン未満
      - up to nect minor / 次のマイナーバージョン未満
  - 依存ライブラリのアップデート
    - Package.resolvedに解決したライブラリのハッシュが記録される
  - パッケージのコンフリクトを解決する
    
- 感想
  - CococaPods/Carthageのようにビルド速度に影響する?

- メモ

# Lab

パフォーマンスLabでGCDのパフォーマンスに関する質問をした

過去の参考になりそうなセッション
https://developer.apple.com/videos/play/wwdc2017/706/


# 223_Expanding the Sensory Experience with Core Haptics

- 内容
  - iOS13でCore Haptic APIが利用できるようになった
  - サッカーボールを蹴った時のCauseとEffect
  - Confirmationの音
  - Harmony
    - 現実世界のようにデジタルの世界でもVisual、Audio、Hapticを組み合わせる
    - タイミングのSynchronizationも重要
  - WatchのクラウンのHaptic
  - Utility
    - ARでも対象に近づくにつれて音を大きくすると（タイマー音など）
  - 3つの原則
    - Causality
    - Harmonu
    - Utility
  - Hapticの付け方
    - ピーク音に合わせる
    - ソフトな音は連続的に変化させる方法も
    - 明確なルールはない
    - Hapticを先に動かして音声を後に流す手法もある

- 感想
  - 技術的なAPIの話はなかったので参加するセッションを間違えた、Hapticでもいろんな種類があることはわかった
  - デザインよりのセッションだったので感覚的な内容が多くて理解が深まらなかった
  - どうやらHapticフィードバックを連続的に実行できるようになったっぽい
  

- メモ