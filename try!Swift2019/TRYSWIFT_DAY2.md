# try! Swift 2日目

## 魔法の法則 @davedelong
  - Appleの人
  - Brandon Sanderson
    - お気に入りのファンタジー作家
    - 日本語になっている本もある
    - 面白い本を書くときの法則
  - 十分に高度な技術は魔法と区別が付かない
    - iPhone端末も魔法
  - 魔法の第一法則
    - ユーザーに何が起きているのか理解してもらう必要がある
    - その責任は作者にある
    - 質問を予想する
    - 解決策へのガイド
    - どうやって?（ここでいうユーザーはライブラリの開発者）
      - Swiftの型システムを利用する
      - 規則に従って慣れ親しんだパターンを使う
      - ヘルプやエラーメッセージ
      - ドキュメントとユニットテストが完全であること
    - fatalErrorで知らせる（実行時エラーまでわからない）
    - @available でコンパイル時にもエラーで知らせる
      - コンパイラによる自動Fixで開発者を教育
      - ドキュメントで案内
  - 魔法の第二法則
    - 制限は権力よりも重要
    - できないことはできることよりおもしろいことが多い
      - 物語での登場人物の制約（できないこと）
        - スーパーマンの弱点
      - 制約は創造的であることを強制する
    - 時間、チーム、個人の能力
      - 制約を元に我々は行動する
      - 創造性を発揮して制約を乗り越える
      - 制約によって本来考えなかった選択肢が登場する
  - 魔法の第三法則
    - 新しいものを使う前に既に持っているものを拡張する
    - 隠された深さを探すことはエキサイティング
    - 他の人が見つけていないものを見つけられる
    - 一見単純であり、しかも奥深い
    - コードのリファクタリングもその一つ
    - 検討していないユースケースは?
    - サポートされていない機能は?  

## ポートレートモードを自作しよう @koooootake
  - ポケモンマスター
  - DeNAマンガボックスの開発
  - iOSのカメラアプリのポートレートモードで背景ぼかせる
    - 深度情報（Depth）を使っている
  - Depthがないときは?
    - 2次元画像を映えさせたい
    - 被写体と背景の分離をDepthを使わずにする
      - CoreMLではうまくいかなかった
      - キャラクラー毎に学習が必要
    - グラブカット?とリタッチで
    - あとは背景をガウシアンブラーでぼかす
    - 被写体の縁がぼかした時に背景にあふれるので被写体を消す
    - 被写界深度も調整できるようにした
  - Demoアプリ
    - https://github.com/koooootake/Portrait-without-Depth-ios

## Swiftでソーシャルネットワークをつくろう @dokun24
  - 二人で発表
    - Ian: IBMのテクニカルリード、Swiftコミッター、Kitura（キトラ）の開発
    - David: モバイル開発者、IBMデベロッパーアドボケイト
  - モバイルバックエンド
    - Standalone
    - MBaaS
    - Bespoke（サーバーサイドSwift）
  - Microservices
    - コンパイル済みバイナリなので起動が早い
    - Javaなどよりメモリ使用量が少ない（コスト削減になる）
    - 相互互換性
  - 一例
    - Allegro
  - docker/HELM/kubernetes
  - OPENAPIは何してくれるか
    - Kituraが自動生成したAPIドキュメント
    - OPENAPIのエコシステムが強み
    - Swift Server Working Group（SSWG）
    - Language Server Protocol（LSP）
  - 本を書いたよ「Server Side Siwft with Kitura」
  - Demo
    - EmojiJournal
    - Xcodeを利用せずにアプリをビルドする
    - シミュレーターで実行
    - VSCodeでLSPを利用したコーディング、自動コード補完
    - OPENAPIのAPIドキュメントを見る
    - OPENAPIUI
    - サーバーのデバッグが簡単にできる
    - WebSocket技術を利用、アプリとブラウザでリアルタイムに更新される
  - 本番系で使えるの？
    - onlineswiftplayground.runでKituraが使われている
      - http://onlineswiftplayground.run/
    - www.agenda.comもKitura
      - https://www.agenda.com/
    - ドイツのIoTバンキング
      - https://bankingofthings.io/
    - CPU/RAMの消費量も悪くないというグラフ
  - http://ibm.biz/trykitura

## 休憩

## Swift Hardware Hacking @mostgood
  - Geany（IDE、Swiftは非対応）
  - v2ではユーザー認証とコンセント電源に対応
  - 回路についてのお話
    - ラズベリーパイ
    - GPIO(General-purpose input/output)
    - SwiftyGPIOというライブラリを使う
      - https://github.com/uraimo/SwiftyGPIO
    - Relayはスイッチ
    - デジタル信号、電圧でオンオフ、1 = 3.3v / 0 = 0v
    - アナログ信号
    - MCP3008（8チャネルのA-Dコンバータ）
  - 光の量で開いてるかしまっているかを検知 
  - 荷重センサーで金額を計算する（抵抗値の変化）
    - HX711
    - アナログ信号は0/1だけではない
    - アナログ信号をどうデジタル信号にするか
      - バイナリ
      - 12bitなど情報の長さを決めておく
        - 24bitなら24回ループして1bitずつ読み込む
  - Bluetooth（BLE）
    - Central（iOS）とPeripheral（ラズパイ）
    - GATT Profile
      - https://www.bluetooth.com/ja-jp/specifications/gatt/generic-attributes-overview
    - CoreBluetooth
  - 全体構成

## SwiftSyntax で便利を実現する基礎 @orga_chem
  - SwiftSyntaxで静的検査やコード生成ができる
    - https://github.com/apple/swift-syntax
  - コードを読み書きしやすいデータにする
    - if文は条件と複文からなる
    - Optional束縛条件
    - 木構造
    - 構文木
    - オレオレSwiftLintが作れる
  - コード生成
    - SwiftSyntaxのRenameRewriterクラスで書き換え
  - これ面白そう！

## Swift type metadata @kateinoigakukun

## モバイルのデザインシステムを構築する @krstnfx

## ランチ

## iOS端末を利用した心理学研究の背景と展望

## SwiftCheckで始めるProperty-based Testing

## All about linking libraries

## 賢者のString

## 休憩

## アセンブリ、君ならできる！

## Swiftコンパイラにコントリビュートする

## Core Dataを守るために

## 次へつなごう— Extending a hand to the next generation of Apple developers

## Party
