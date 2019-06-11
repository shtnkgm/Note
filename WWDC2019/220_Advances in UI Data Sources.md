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
  - insertItems / moveItems / appendItems /  appendSectionsでデータソースを更新する
  - パフォーマンスも高速
  - applyはバックグラウンドキューで実行しても安全
  - これがベストなAPI！！
  - iOS13のシェアシートの内部実装でも利用している

- 感想
  - SwiftUIが発表された中、UIKitのセッションだが実用的な内容でプロダクトにも反映できそう
  - アニメーションが自動なのも良い

- メモ
  - https://developer.apple.com/documentation/uikit/views_and_controls/collection_views/using_collection_view_compositional_layouts_and_diffable_data_sources?changes=latest_minor
  - https://developer.apple.com/documentation/uikit/uicollectionviewdiffabledatasource
  - https://developer.apple.com/documentation/uikit/uitableviewdiffabledatasource
