# 237_Building Custom Views with SwiftUI

- 内容
   - レイアウト処理の基本
      - 親Viewは子Viewに対してサイズを提案する
      - 子は自身のサイズを選択する
        - Image("hoge").frame(width: 50, height: 10)
        - Image("hoge").aspectRation(1)
        - Text("hoge")
      - 親Viewは子Viewを親Viewの座標空間に配置する
      - SwiftUIは座標を最も近いピクセルに丸める
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
