# 237_Building Custom Views with SwiftUI

- 内容
   - 親Viewから子Viewのレイアウト処理の流れ
   - HStackのViewのレイアウト方向はロケールによって自動で変わる
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
   - Viewのレイアウトの仕組みがわかるセッションなので、レイアウトが上手くいかない時に見直すと良さそう
   - SwiftUIの拡張方法を色々知っておくと、インタラクティブで自由度の高いコーディングができそう

- メモ
