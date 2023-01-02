# JSTQB FL メモ

## 第1章 テストの基礎

### 1.1 テストとは何か

1. テスト実行に際してやること
2. テストの目的
3. テストとデバッグの違い
4. テストが貢献すること
5. エラー、欠陥、故障

#### テスト実行に際してやること

- テスト実行前にすること
  - テスト計画
    - リソース配分、タスクの締め切り設定、テスト修了基準
    - （主にテストマネージャーがやる）
  - テスト分析
    - テストベース分析（？）
    - 何をテストするのか決める
  - テスト設計
  - テスト実装
    - テストの実行に必要なものすべてを準備する
- テスト実行中にすること
  - 実行結果のチェック
  - 修了基準を満たしているかの評価
  - *妥当性確認*
- テスト完了したらすること
  - ステークホルダーへの報告
    - 実行結果、欠陥への対応結果、終了基準の達成度合い
    - *テストウェア（？）を資産化*

#### テストの目的

いろいろ

#### テストとデバッグのちがい

- テスト
  - ソフトウェアに存在する欠陥に起因する故障を発見することが目的
- デバッグ
  - 故障のもととなる欠陥を見つけて、欠陥の原因を解析し、修正する開発の活動
  - 修正したら再度テストする

#### テストが貢献すること

- 要求分析
  - ユーザー要求やユーザーストーリー
- システム設計
  - 設計内容
- コード開発、コンポーネントテスト
  - 開発担当者と連携してコードと対になるテストケースの両方をレビュー
  - コンポーネントテストは開発担当者自身が行うことが一般的
- 結合テスト、システムテスト、受入テスト

#### エラー、欠陥、故障

A person can make an error(mistake), which can lead to the introduction of a defect (fault or bug) in the software core or in some other related work product.

- エラー（誤り）
  - 間違った結果を生み出す人間の行為
    - 勘違い、思い込み、誤解
    - 納期、プレッシャー、人間の性質、コードが複雑、経験、コミュニケーション
- 欠陥（defect）
  - 作業成果物に存在する、要件または仕様を満たさない不備または欠点
- 故障（failure）
  - コンポーネントやシステムの欠陥が原因で期待結果が得られないこと
  - 期待結果の記載が違う場合は偽陽性
    - 偽陰性に気を付ける

### 1.3 テストの7原則

exhaustive, testing everything, is impossible.

#### トレーサビリティ

テストベースとテスト作業成果物との間のトレーサビリティ

- 方法
  - トレーサビリティマトリクスの作成
  - 要求管理ツール
  - ALM（application lifecycle management）
- メリット
  - ステークホルダーやマネジメント層への説明にも
    - テストそのものの合理性（監査）
    - 健全性（ITガバナンス）
    - 整合性（影響度の変更への追随）
    - 十分性（カバレッジ的な）
    - 理解度

#### テスト分析

- テスト対象の機能要件、非機能要件、構成、構造、ソフトウェアの設計情報などが記されたテストベースを収集
- 情報の取捨選択、再収集、新たに作成するか検討
- テストレベルごとに適切な分析をする
  
#### テスト分析の成果物

- テスト条件と、そのもととなるテストベースとトレーサビリティをとっておく
- テスト条件自体の過不足を確認できるようにしておく

### keywords

- reverse engineering
  - a process for determining the source code from the object code

## 第2章 開発ライフサイクル全体を通してのテスト

### 2.1.1

in ANY software development lifecycle model,

- for every development activity, there is a corresponding test activity
- each test level has test objectives to that level
- test analysis and design for a given test level begin during the corresponding development activity
- testers participate in discuttions
  - define/refine requirements
  - design
  - reviewing work products asa drafts are available

#### lifecycle model

- sequential development model
  - development process as a linear/sequential flow
  - next phase starts after previous phase gets completed
  - no overlap phase
  - beneficial to have early feedback from following phase
- waterfall model
  - activities are completed one after another
  - test activities only occur after all other development activities
- V-model
  - integrates the test process throughout the dev process
    - implement the principle of early testing
  - includes test levels associated with each corresponding dev phase
    - supports early testing
  - execution of tests associated with each test level proceeds sequantially but in some cases overlapping occurs
- Incremental dev
  - irequirements/design/build/testing establihed in pieces
    - software's features grow incrementally(=徐々に)
- Iterative dev (=反復)
  - group of features are specified ~ tested in a series of cycles
  - each iteration delivers working software
    - growing *subset* of the overall set of features until final

### テストの種類

- 結合テスト
  - コンポーネント結合テスト
  - システム結合テスト
- テストタイプ
  - 機能テスト
  - 非機能テスト
  - ホワイトボックステスト
  - リグレッションテスト
  - *regression = デグレ*
目的：内在する欠陥を検出する、機能的/非機能的？振る舞いが設計及び仕様通りである、品質が信頼できるものである、など  
仕様書、設計書などをもとに作成する  

- 受入テスト
  - ユーザー受入テスト
  - 運用受入テスト
  - 契約・規制による受入テスト

- 機能テスト（*what*）
  - 必要になる知識
    - ソフトウェアが解決する特定のビジネス問題
    - ソフトウェアが果たす役割
- 非機能テスト（*how*）
  - 計測可能な項目（例：応答時間）
  - 評価可能な値（例：3秒）
  - テストの種類
    - performance testing
      - load testing
      - stress testing（リソースの低減も含む）
    - usability testing
      - 特定のユーザーが特定の使用状況の下でシステムを使用する際の有効性、効率性、満足度合
    - interoperability testing
      - 相互運用性テスト
      - 2つ以上のコンポーネントやシステムが情報を交換でき、すでに交換された情報を使用できる度合
    - maintainability testing
    - reliability testing
    - potrability testing
    - securily testing
  - 必要な知識
    - 設計や技術に特有の弱点
      - プログラミング言語の特徴など
    - 特定のユーザーの知識
      - 利用シーンや利用のタイミング
- ホワイトボックステスト
  - テストベース
    - コード、アーキテクチャ、ワークフロー、システム内のデータフロー
  - カバレッジ出しやすそう
  - 必要になる知識
    - コードのビルド方法
    - データの格納方法
    - カバレッジツールの使用、解釈方法

### メンテナンスの影響度分析

困難になる要素

- 仕様が最新版でない、存在しない
- テストに関するドキュメントが古い、存在しない
- テスト/テストベースのトレーサビリティが維持されていない
- ツールのサポートが乏しい
- ドメイン/システムの知識が乏しい
- 開発時に保守性が考慮されていない

## 第3章 静的テスト（static testing）

↔  動的テスト（dynamic testing）: error guessing 含む

### 静的テストで見つけやすい欠陥

- requirement defects
  - inconsistencies, ambiguities, contradictions, omissions, inaccuracies, redundancies
- desigin defects
- coding defects
- deviations from standards
- incorrect interface specifications
- security vulneravilities
- gaps or inaccuracies in test basis traceability or coverage

### レビュー技法の適用

- アドホック
- チェックリストベース
- シナリオとドライラン
  - 成果物と期待する使い方
  - 最初からシステムを動かすイメージでレビュー
- ロールベース
  - パースペクティブベース
    - ロールベースの一つ。要件や技術的な作業成果物の場合など

#### 3.2.2 roles and responsibilities

- author
  - creates the work product
  - fixes defects in the work product
- management
  - responsible
    - review planning
    - review execution
  - monitors ongoing cost-effectiveness
  - executes control decisions
- facilitator (moderator)
  - ensure
    - effective review meeting
  - mediates between the various points of view
  - success of the review depends on them
- review leader
  - responsible
    - overall of the review
  - review member, organize
- reviewers
  - experts, people working on the project, stakeholders
  - identify defects
  - deffirent perspective
- scribe (recorder)
  - collate potential defects
  - records new potntial defect

## 第5章 テストマネジメント

### 独立したテスト

- 開発担当者自身がテスト
  - 熟知している分欠陥を見つけやすい
  - 先入観、確証バイアス
- 開発チーム内で行うテスト
  - 外部チームより成果物の理解がある
  - 心理面で独立した視点を持てない
- など

#### 独立したテストのメリット

- 開発担当者と異なる背景、技術的視点、バイアス
- 開発やりとりの仮定について、検証、説明の要求、反証ができる

#### デメリット

- 隔絶、協力関係の欠落、遅延、対立
- 責任感が薄れる
- ボトルネックとして見られる、リリース遅延
- 重要な情報が漏れやすい

### テストレポート

- 目的
  - 以下をそれぞれのステークホルダーに周知すること
    - テスト活動の結果の要約
    - テスト活動から得られた教訓をメンテナンスフェーズや未来のプロジェクトなどの活動に生かすための情報
- 種類
  - 進捗レポート
  - サマリーレポート
- 内容
  - 例）実施したテスト
    - 実行したテスト
    - 逸脱
    - 完了評価
    - 進捗を妨げた要因、対応策
    - テスト方法
    - 残存リスク
    - 成果物
    - 再利用可能なテスト資産
- 読み手
  - 各ステークホルダー
  - 開発担当者
  - テストチーム
  - プロジェクトマネージャー
  - 経営者

### リスクとテスト

#### リスク

将来的に否定的な結果となる事象が起きる恐れを含む。リスクのレベルは可能性と影響（損害）で決まる。  

- プロダクトリスク
  - 成果物がユーザー/ステークホルダーの正当なニーズを満たすことができない恐れ
- プロジェクトリスク
  - 発生した場合にプロジェクトの目的達成に悪影響を与える

### 欠陥マネジメント

- 不正（anomaly）
  - 期待結果と違う気がするが欠陥に対して調査が必要なもの

### テストで使用するメトリクス

特定の値を取得することでテスト活動の指針に生かせる

#### 指針

- 予算、スケジュールの進捗
  - 確認、フィードバック
- 実施中のテスト対象の品質
- テストアプローチの十分性
- テスト目的に対するテスト活動の効果

- metrics-based
  - metrics of former similar projects
  - typical values
- expert-based
  - experience of the owners of the testing tasks
  - by experts

#### メトリクス例

- テストケースの準備完了割合
  - 試験設計完了度合
- テスト環境の準備完了度合
  - 試験中ステータス
- テストケースの実行
  - 実施中の数、実施完了数
- 欠陥情報
  - 欠陥密度、検出/修正した欠陥、故障率、確認テストの結果
  - テスト実行の優先順やリソースの調整
- 要件、ユーザーストーリー、受け入れ基準、リスク、コードのテストカバレッジ
- タスクの完了、リソースの割り当てと稼働状況、工数
- テストに費やすコスト

### 5.2.2 テスト戦略

- 分析的戦略
  - 要件やリスクなどの要因を分析
  - リスクや優先度が高いところからやるリスクベースドテストも
- モデルベースド戦略
  - モデル：ビジネスプロセス、機能、内部構造、状態遷移モデル、信頼度成長モデル（故障率）、運用プロフィール（使い方）など
- 系統的戦略
  - あらかじめあるテストケースや条件
    - チェックリスト
    - 発生しやすい故障リスト
    - 重要とされている品質特性ベース
- プロセス準拠（標準準拠）戦略
  - 企業内外の標準
  - 業界固有の標準
- 指導ベース（コンサルテーションベース）戦略
  - 外部のステークホルダー、専門家からの指導
  - エンドユーザーの意見に基づいてビジネスプロセスをテストする場合も
- リグレッション回避戦略
  - ＝デグレ回避できるようデグレがないか優先的に確認する
  - 標準テストスイートがあれば再利用したり、自動化したり
- 対処的戦略
  - テスト実行時の状況にあわせて行う
  - 探索的テストはここ
  
### 第6章

#### テストツールの分類

- management
  - test / application lifecycle (ALM)
  - requirements
  - refect
  - configuration
  - continuous integration
- tool support for static testing
  - static analysis
- tool support for test design and implementation
  - create the maintainable work products in test design, implementation, test cases, test procedures, test data.
    - model-based testing
    - test data preparation
- test execution and logging
  - test execution
  - coverage
  - test harness
- performance measurement and dynamic analysis
  - performance testing
  - dynamic analysis toolss
