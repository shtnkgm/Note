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
