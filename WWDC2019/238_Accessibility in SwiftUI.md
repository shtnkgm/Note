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
