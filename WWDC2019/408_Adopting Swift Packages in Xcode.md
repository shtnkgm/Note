# 408_Adopting Swift Packages in Xcode

- 内容
  - Xcode11からSPMに直接アクセスできるように
  - SPMでパッケージを導入するデモ
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

パフォーマンスLabでGCDのパフォーマンスに関する質問をした

過去の参考になりそうなセッション
https://developer.apple.com/videos/play/wwdc2017/706/
