# 237_Building Custom Views with SwiftUI

- 内容
   - 親Viewから子Viewのレイアウト処理の流れ
   - HStackのViewのレイアウト方向はロケールによって自動で変わる
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
   - Viewのレイアウトの仕組みがわかるセッションなので、レイアウトが上手くいかない時に見直すと良さそう
   - SwiftUIの拡張方法を色々知っておくと、インタラクティブで自由度の高いコーディングができそう

- メモ

# 238_Accessibility in SwiftUI

- 内容
  - SwiftUIでのアクセシビリティ実装について
  - Voice controls
  - Full Keyboard Access
  - アクセシビリティは全ての人のためのもの
  - Label/Value/Trait,Role/Default Action/Custom Action
    - Labelは理解しやすくする
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
    - .accessibility(trait:)
    - .accessibility(value:)
    - .accessibilityAction(named:) { }
    - 色のコントラストを確認するアプリでのデモ
    - .accessibility(visibility:)

- 感想
  - ButtonStyleプロトコルとか用意されてるし、デザインシステムの導入もSwiftUIだとやりやすそう
  - 新しいAccessibilityを使ってイメージが湧いてから動画を見直すと良さそう

- メモ

# 

- 内容

- 感想

- メモ

# 

- 内容

- 感想

- メモ