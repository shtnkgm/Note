# 401_What's New in Xcode 11

  - Editorモード
    - Source Control Hisotry
    - Editor Options
    - Add Editor
  - Demo: Workflow Updates
    - SwiftUIプレビューの仕方
    - Optionでエディタを追加する方向を下に変更
    - Windowとタブ移動のショートカット
    - 全画面でのフォーカスモード
    - ミニマップ
      - Findでの文字列検索と連動
    - Add Documentation（元から）
      - typoの修正も連動
    - Show Changeでインラインdiff
 - ソースエディターの進化
    - コード補完がより強力に
    - Function Mode
 - Swift Package Manager
    - XCodeに統合
    - Bitbucket/Github/GitLab
    - プロジェクトにタブ追加
    - GUIで操作、バージョン、ブランチ指定
    - ライブラリソースも参照可能
 - git
    - Stach changes
    - Cherry-Pick
    - History Inspecterがどんなファイルでも開けるように
 - デザインツール
    - storyboardでDarkMode切り替え
    - Custom Symbols
    - ローカライズ
    - アイコンをFontにする
    - Dark Modeでの画像、色の切り替え（Asset）
    - Environment Overrides（実行時にDynamicTypeやアクセシビリティ設定を変更可能）
 - デバッグ
    - Device Condition
 - Testing
    - Test Plan
    - 複数言語でのローカライズテスト
 - シミュレーター
    - Watchだけ起動
    - メタル実行
    - CPU使用90%減
    - Warm boot
 - Insturuments
    - sign post（Xcode10）
    - Metalのトレース分析が10倍に
    
# 402_What's New in Swift

 - Binary Frameworks
    - ABIモジュールスタビリティ
    - Application Binary Interface
    - これがないと同じコンパイラでビルドされている必要がある
    - Swift5以降であればバラバラのコンパイルでOK
    - Module Stabilityとは
    - .swiftinterface,（modue interfaceファイル）
    - Module + ABI Stability = Binary Frameworks
 - Swift Package Manager
 - パフォーマンス
    - Shared Swift Runtime
    - 起動時間のオーバーヘッドはゼロ
    - コードサイズも10%〜15%削減される
    - SiwftとObjective-Cのブリッジ処理も高速化
    - String
 - SourceKit
    - Language Server Protocol
    - oss: https://github.com/apple/sourcekit-lsp
 - Swift言語とスタンダードライブラリ
    - https://github.com/apple/swift-evolution
    - Implicit Return
    - structの一部のプロパティでの初期化
    - SIMD型（固定長ベクトル、行列）、SIMDMask
    - StringInterpolation（ExpressibleByStringInterpolation）
    - Opaque Result Types（some）
    - Property Wrapper Types（@propertyWrapper）
    - DSLs
      -  
      - closureとメソッド呼び出しで構造を記述
      - 制御構文も記述可能  
      - @HTMLBuuilder
      
# 204_Introducing SwiftUI: Building Your First App

  - StackにEmbedしたりできる
  - GUI操作で角丸にする
  - コマンドクリックでExtractViewが便利そう
  - 画像のリサイズもImage ResizeのGUIから、コードなら.resizable()
  - Previewでナビゲーションをチェックしたい場合、NavigationView { } でくくる 
  - @State / @Binding / @EnvironmentObject
  - tapAction { }でタップ時の処理を記述
  - withAnimation { }でアニメーションを有効にする
  - HStack、VStack、ZStack
  - Group { }で複数のプレビューを表示
  - BindableObject、@ObjectBinding
  - NavigationView { } 
  - List { }
  - Section { }
  - ForEach() { }
  - onDelete(perform:)
  - onMove(perform:)
  - listStyle(.grouped)
  - environment(\.colorScheme: .dark)
    - sizeCategory
    - locale
    - layoutDirection
    
 - INMediaIntent
 - INAdd
 - INSearchForMediIntent
 
# SWIFT Open Lab
 
 @_exported import Core
 
 *** Terminating app due to uncaught exception 'RLMException', reason: 'Primary key property 'name' does not exist on object 'RealmSwiftPermissionRole''
 
# 209_What's New in Machine Learning
 
  - CreateML
    - CreateMLでの画像分類のデモ
      - Developer Toolから開ける
      - 65個の5種類の花の画像
      - Augumentation（前からあるやつ）
      - 前よりGUIが使いやすくなったかも
    - 音声分類
      - ギターなのか拍手なのか
    - アクティビティ分類
    - テキスト分類
    - Word Tagger
    - Tabular Classifier
    - Recommender
  - Domain APIs
    - Image Saliency
      - Document Cameraのサンプル
    - Natural Language
      - 感情分析
      - Word Embeddings
    - Speech and Sound
      - オフライン音声認識
    - 組み合わせ
      - 類義語検索
    - On Deviceのメリット
    - CoreML3
      - Model Flexibility
        - Instance Segmentation
        - TensolFlowとONNXからのコンバーター
      - Model Personalization
        - FaceIDも同じようにパーソナライズされている
        - My Dog
        - サーバーベースのアプローチはプライバシーの問題あり
        - コストもかかる
        - On Deviceのアプローチ
        
# 704_Core ML 3 Framework