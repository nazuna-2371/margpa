# Governance Definitions 一覧

このarchitectureの中心は、ファイル配置ではなく、責務分離である。  
MARGD Runtime Governance Bundle は、AIの複雑な応答や判断を、1つの巨大な指示や万能domainで処理するのではなく、  
複数のGDへ分割し、必要に応じて動的に組み合わせるための構造である。

この文書では、MARGD Runtime Governance Bundle Prototype に含まれる16個の Governance Definitions を一覧する。

ここでの目的は、各GDの詳細仕様を説明することではない。  
それぞれのGDが何を扱い、何を扱わないかを、初見でも把握しやすい粒度で整理する。

---

## 1. この文書で扱うもの

この文書で扱うGDは、次の16個である。

```text id="2rv0f2"
CDOGD

SPPGD
DAAGD
SDAGD
SDMRGD

DSGD
ACRGD
AAGD
AISGD
MPGD
DCAGD
PMOGD
AIRGD
AIAGD
SEGD
OMRGD
```

ARGD / DAGD は、このprototypeの前提となるcore governanceである。  
ただし、この文書では16個のGDには含めない。

ARGD / DAGD の詳細は、repository root側のREADMEおよび既存資料を参照すること。

---

## 2. 全体の分類

本prototypeでは、16個のGDを次のように整理する。

```text id="jtp3me"
横断調整:
  CDOGD

判断pipeline:
  SPPGD
  DAAGD
  SDAGD

条件付きwatchdog:
  SDMRGD

ordinary:
  DSGD
  ACRGD
  AAGD
  AISGD
  MPGD
  DCAGD
  PMOGD
  AIRGD
  AIAGD
  SEGD
  OMRGD
```

この分類は、GDの性質を説明するためのものである。  
分類順や記載順は、優先度、起動順、権限の強さを意味しない。

特に、ordinaryに置かれるGDは、各専門領域の意見・判断材料・確認条件を出すためのGDである。  
ordinaryのGDは、実行許可、最終決定、承認、責任主体の割当を行わない。

自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態などの authority / accountability 判断は DAAGD が扱う。

---

## 3. CDOGD

### 3.1 基本情報

```text id="zjm95v"
略称:
  CDOGD

正式名称:
  Cross-Domain Orchestration Governance Definition

配置先:
  definitions/orchestration/cdogd_v0.1.0_en.json
```

### 3.2 役割

CDOGD は、複数のGDを横断してまとめるための自動動的ルーティングのオーケストラGDである。

現在の依頼や対象に応じて、どのGDをどの範囲で働かせるかを整理する。  
また、GD同士の重なり、引き渡し、抑制、弱化、修復の伝播を扱う。

```text id="l5ex5j"
CDOGDが扱うもの:
  関係しそうなGDの候補
  起動する範囲
  それぞれのGDの役割
  GD同士の重なり
  GD間の引き渡し
  修復の伝播
  抑制
  弱化
```

### 3.3 扱わないもの

CDOGDは、最終決定を行わない。  
承認、実行許可、責任主体の割当、専門判断そのものも行わない。

```text id="0rm4rn"
CDOGDが扱わないもの:
  最終決定
  承認
  実行許可
  責任主体の割当
  専門判断の代替
```

---

## 4. Decision Pipeline Domain Extensions

判断pipeline系GDは、判断材料を最終判断に近づける過程を分離するためのGD群である。

```text id="bypwa7"
SPPGD:
  戦略判断の構造を整理する

DAAGD:
  MARGD内で authority / accountability 判断を担当する
  自律判断として扱えるか、人間判断へ戻すべきか、承認待ちか、委任範囲外か、責任主体未確定かを判断する

SDAGD:
  SPPGDの判断構造と、DAAGDが判断した authority / accountability state を監査する
  DAAGDを代替しない
  自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態を判断しない
```

ordinaryのGDなどから出た専門的な判断材料は、そのまま最終判断になるわけではない。  
必要に応じて、SPPGDが判断構造を整理し、DAAGDが authority / accountability 判断を行い、  
SDAGDがその判断構造と authority / accountability state を監査する。

---

## 5. SPPGD

### 5.1 基本情報

```text id="c1nd16"
略称:
  SPPGD

正式名称:
  Strategic Planning and Prioritization Governance Definition

配置先:
  definitions/domain_extensions/decision_pipelines/sppgd_v0.1.0_en.json
```

### 5.2 役割

SPPGD は、戦略判断の構造を整理するGDである。

目的、前提、制約、選択肢、選ばなかった選択肢、優先順位、配分、順序、継続、停止、撤退、保留、再評価条件などを整理する。

```text id="ji0io1"
SPPGDが扱うもの:
  目的
  前提
  制約
  選択肢
  選ばなかった選択肢
  優先順位
  配分
  順序
  継続
  停止
  撤退
  保留
  再評価条件
```

### 5.3 扱わないもの

SPPGDは、最終決定を行わない。  
判断権限、承認、責任主体、戦略判断の監査も扱わない。

```text id="8ov35w"
SPPGDが扱わないもの:
  最終決定
  判断権限の判定
  承認
  責任主体の割当
  戦略判断の監査
```

---

## 6. DAAGD

### 6.1 基本情報

```text id="uu1ms2"
略称:
  DAAGD

正式名称:
  Decision Authority and Accountability Governance Definition

配置先:
  definitions/domain_extensions/decision_pipelines/daagd_v0.1.0_en.json
```

### 6.2 役割

DAAGD は、MARGD内で判断権限状態を判断する authority / accountability GD である。

DAAGDは、既存のsystem policy、developer policy、runtime policy、tool権限、外部実行権限、委任条件、承認条件、責任分界に基づき、  
当該判断をAIまたはruntimeの自律判断として扱えるか、人間判断へ戻すべきか、承認待ちとして扱うべきか、委任範囲外として扱うべきか、責任主体未確定として扱うべきかを判断する。

ただし、DAAGDは外部に存在しない権限を新しく生成するものではない。  
DAAGDは、既に存在する方針、権限、委任、承認条件、責任分界の範囲内で、MARGD内の authority / accountability state を判断する。

```text id="6t5n3t"
DAAGDが扱うもの:
  判断権限
  承認条件
  委任範囲
  責任主体
  判断者
  実行者
  AI判断の権限分類
  人間承認の要否
  差し戻し条件
  記録条件
```

ordinaryのGDが専門的な判断材料を出しても、それをAIが採用してよいとは限らない。  
その判断材料をAIが使ってよいか、人間判断に戻すべきか、承認が必要か、誰が責任を持つかは DAAGD が扱う。

### 6.3 扱わないもの

DAAGDは、判断内容そのものを作らない。  
SPPGDの判断構造を作らず、SDAGDの監査も代替しない。  
また、DAAGD自身が新しい権限を生成するわけではない。

```text id="ffpk5d"
DAAGDが扱わないもの:
  判断内容の生成
  判断構造の生成
  専門判断の代替
  実行作業の代替
  戦略判断の監査
  自己承認
  権限の生成
```

DAAGDは、既に存在するruntime policy、委任範囲、人間承認条件、責任主体などをもとに、判断権限の状態を扱うGDである。

---

## 7. SDAGD

### 7.1 基本情報

```text id="n3pw24"
略称:
  SDAGD

正式名称:
  Strategic Decision Audit Governance Definition

配置先:
  definitions/domain_extensions/decision_pipelines/sdagd_v0.1.0_en.json
```

### 7.2 役割

SDAGD は、戦略判断に関する監査を担当するGDである。

SDAGDは、SPPGDが整理した判断構造と、DAAGDが判断した authority / accountability state を監査する。

SDAGDが示すのは、あくまで監査上の状態である。  
SDAGDは、戦略判断そのものを作らず、DAAGDを代替せず、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態を判断しない。

```text id="xiw51c"
SDAGDが監査するもの:
  SPPGDの判断構造
  DAAGDが判断した authority / accountability state
  判断前提
  制約
  権限根拠
  承認条件
  責任主体
  未解決事項
```

SDAGDは、監査上の状態として、監査上の重大な阻止条件なし、条件付き監査所見あり、修復戻し、監査上の無効化などを扱う。

これらは監査状態であり、正式な承認、実行許可、最終意思決定、責任主体の確定そのものではない。

### 7.3 扱わないもの

SDAGDは、戦略判断そのものを作らない。  
判断権限も作らず、実行作業も行わない。  
また、SDMRGDの監査状態を承認するGDでもない。

```text id="8nr9fw"
SDAGDが扱わないもの:
  戦略判断の生成
  判断権限の生成
  実行作業
  SDMRGDの承認
```

---

## 8. SDMRGD

### 8.1 基本情報

```text id="y6vizo"
略称:
  SDMRGD

正式名称:
  Strategic Decision Meta-Review Governance Definition

配置先:
  definitions/domain_extensions/conditional_watchdogs/sdmrgd_v0.1.0_en.json
```

### 8.2 役割

SDMRGD は、SDAGDの監査状態をメタレビューするGDである。

SDAGDの監査範囲、監査根拠、監査結果分類、形式的通過の危険、過剰監査、過少監査、修復の必要性などを確認する。  
SDMRGDにおけるエスカレーションは、外部の最終判断や承認へ直接進めることではない。  
基本的には、SDAGD側の自己監査、修復、再監査、または上位runtime側の条件確認へ戻すことである。

```text id="tlzfvu"
SDMRGDが見るもの:
  SDAGDの監査範囲
  SDAGDの監査根拠
  監査結果分類
  形式的通過の危険
  過剰監査
  過少監査
  DAAGD領域への越境
  修復必要性
```

### 8.3 扱わないもの

SDMRGDは、戦略判断そのものを直接監査しない。  
SDAGDの主監査を代行せず、最終決定も行わない。

```text id="jc2gcb"
SDMRGDが扱わないもの:
  戦略判断そのものの監査
  SDAGDの主監査の代行
  判断権限の判定
  最終決定
  相互監査ループ
```

---

## 9. Ordinary Domain Extensions

ordinary系GDは、各専門領域の観点から、専門的意見、判断材料、確認条件、検出結果、引き渡し材料を出すGD群である。

ordinary系GDは、実行許可、最終決定、承認、責任主体の割当を行わない。

```text id="44wtdi"
ordinary系GD:
  専門的意見を出す
  判断材料を出す
  確認条件を出す
  検出結果を出す
  引き渡し材料を出す

ordinary系GDが扱わないもの:
  実行許可
  最終決定
  承認
  責任主体の割当
```

---

## 10. DSGD

### 10.1 基本情報

```text id="224uqy"
略称:
  DSGD

正式名称:
  Data Science Governance Definition

配置先:
  definitions/domain_extensions/ordinary/dsgd_v0.1.0_en.json
```

### 10.2 役割

DSGD は、データ分析の観点から、分析目的、対象範囲、データ、構造、出所、品質、仮説、手法、評価指標、漏れ、偏り、統計的妥当性、分析主張を扱うGDである。

```text id="nig292"
DSGDが見るもの:
  分析目的
  対象範囲
  データ
  データ構造
  データの出所
  データ品質
  仮説
  手法
  評価指標
  漏れ
  偏り
  予測と因果の区別
  分析主張
  実行履歴
```

### 10.3 扱わないもの

DSGDは、研究主張の新規性、実装品質、成果物構成、進行管理、判断権限を扱わない。

---

## 11. ACRGD

### 11.1 基本情報

```text id="lqsru1"
略称:
  ACRGD

正式名称:
  Artifact Composition and Review Governance Definition

配置先:
  definitions/domain_extensions/ordinary/acrgd_v0.1.0_en.json
```

### 11.2 役割

ACRGD は、成果物の構成、変換、読みやすさ、形式、配置、公開・提出可能性の主張を扱うGDである。

```text id="piicr2"
ACRGDが見るもの:
  成果物の目的
  読者
  情報源の選択
  構成
  変換
  形式
  配置
  読みやすさ
  機械可読性
  秘密情報
  開示範囲
  言語版
  改訂履歴
  公開・提出可能性の主張
```

### 11.3 扱わないもの

ACRGDは、専門内容の正しさや最終承認を扱わない。  
成果物として整っていることは、専門的に正しいことや公開承認済みであることを意味しない。

---

## 12. AAGD

### 12.1 基本情報

```text id="7m5o9t"
略称:
  AAGD

正式名称:
  Agentic AI Governance Definition

配置先:
  definitions/domain_extensions/ordinary/aagd_v0.1.0_en.json
```

### 12.2 役割

AAGD は、Agentic AIの実行過程における目的、作業範囲、計画、手順、tool呼び出し、副作用、作業状態、引き渡し、記憶、完了主張を扱うGDである。

```text id="naxtw8"
AAGDが見るもの:
  目的
  作業範囲
  計画
  手順
  tool呼び出し履歴
  副作用
  作業状態
  checkpoint
  retry / rollback / compensation
  引き渡し
  記憶の根拠
  完了確認
  最終状態
```

### 12.3 扱わないもの

AAGDは、判断権限、安全判断、運用判断、構造設計判断、プロジェクト優先度、成果物品質、GD横断の振り分けを扱わない。

AAGDが実行過程を確認することは、実行許可を出すことではない。

---

## 13. AISGD

### 13.1 基本情報

```text id="qj3x1z"
略称:
  AISGD

正式名称:
  AI Security Governance Definition

配置先:
  definitions/domain_extensions/ordinary/aisgd_v0.1.0_en.json
```

### 13.2 役割

AISGD は、AIを介して発生するAIセキュリティ上の危険を扱うGDである。

```text id="1vwnxt"
AISGDが見るもの:
  プロンプト注入
  脱獄試行
  指示漏えい
  秘密情報の露出
  個人情報の露出
  tool悪用
  agentic takeover
  retrieval poisoning
  memory contamination
  権限混同
  方針回避
  agent間攻撃
```

### 13.3 扱わないもの

AISGDは、一般的なcybersecurity全般、通常のAgentic AI実行、model policy全体、実装、運用、判断権限、戦略判断の監査を吸収しない。

AISGDは安全上の危険を出すが、その後の authority / accountability 判断はDAAGDの領域であり、  
正式な承認や外部実行可否はruntime policy、人間、組織、外部権限主体の領域である。

---

## 14. MPGD

### 14.1 基本情報

```text id="xhy6np"
略称:
  MPGD

正式名称:
  Model Policy Governance Definition

配置先:
  definitions/domain_extensions/ordinary/mpgd_v0.1.0_en.json
```

### 14.2 役割

MPGD は、model policy上の判断について、根拠、適用範囲、例外、記録を扱うGDである。

```text id="2vzn4h"
MPGDが見るもの:
  方針の識別
  条項の識別
  version
  適用可否
  適用範囲
  優先関係
  矛盾
  例外
  危険
  不確実性
  過剰拒否
  過少拒否
  非二択の判断分岐
  再評価
  修復
  改訂
  判断履歴
```

### 14.3 扱わないもの

MPGDは、Agentic AIの実行、AI安全上の脅威分析、成果物品質、最終承認権限を扱わない。

---

## 15. DCAGD

### 15.1 基本情報

```text id="95xfo8"
略称:
  DCAGD

正式名称:
  Development Consulting AI Governance Definition

配置先:
  definitions/domain_extensions/ordinary/dcagd_v0.1.0_en.json
```

### 15.2 役割

DCAGD は、AI支援型の開発相談を扱うGDである。  
要件整理、技術選択肢、設計方針、実装方針比較、実現可能性、概算工数、開発上の危険などを整理する。

```text id="6ydsua"
DCAGDが見るもの:
  要件整理
  技術選択肢
  設計方針
  実装方針比較
  実現可能性
  難易度
  概算工数
  開発上の危険
  保守性
  拡張性
  試作品の範囲
  最小実用版の範囲
  仕様変更の影響
```

### 15.3 扱わないもの

DCAGDは、実装そのもの、test実行、deployment、運用、最終的な安全監査、法務確認、プロジェクト成功保証、組織としての最終判断を扱わない。

---

## 16. PMOGD

### 16.1 基本情報

```text id="3znj90"
略称:
  PMOGD

正式名称:
  Project Management and Orchestration Governance Definition

配置先:
  definitions/domain_extensions/ordinary/pmogd_v0.1.0_en.json
```

### 16.2 役割

PMOGD は、プロジェクト進行の整理を扱うGDである。  
作業項目、担当、期限、依存関係、阻害要因、引き渡し、納品可能性などを整理する。

```text id="xmggky"
PMOGDが見るもの:
  作業項目
  task
  issue
  backlog
  milestone
  担当
  期限
  依存関係
  阻害要因
  引き渡し
  合意事項
  未解決事項
  action item
  納品可能性
  domain横断の作業状態
```

### 16.3 扱わないもの

PMOGDは、戦略判断、技術判断、実装、運用判断、法務・規制判断、成果物品質、正式承認を扱わない。

---

## 17. AIRGD

### 17.1 基本情報

```text id="tw4z62"
略称:
  AIRGD

正式名称:
  AI Research Governance Definition

配置先:
  definitions/domain_extensions/ordinary/airgd_v0.1.0_en.json
```

### 17.2 役割

AIRGD は、AI研究における研究主張、新規性、証拠と主張のつながりを扱うGDである。

```text id="hjpf2v"
AIRGDが見るもの:
  研究課題
  先行研究
  新規性の主張
  仮説
  反対仮説
  反証条件
  研究設計
  証拠
  実行履歴
  結果と主張の分離
  否定的結果
  限界
  再現条件
  公開時の主張の整合性
```

### 17.3 扱わないもの

AIRGDは、Agentic AIの実行、統計的妥当性の詳細、software品質、成果物構成、AI安全上の脅威分析、承認権限を扱わない。

---

## 18. AIAGD

### 18.1 基本情報

```text id="aiagd_basic_info"
略称:
  AIAGD

正式名称:
  AI Architecture Governance Definition

配置先:
  definitions/domain_extensions/ordinary/aiagd_v0.1.0_en.json
```

### 18.2 役割

AIAGD は、AIシステムの構造、構成要素の責務、接続関係、情報の流れ、境界設計、配置、構造上の主張、実行時の整合主張を扱うGDである。

```text id="aiagd_scope"
AIAGDが見るもの:
  システムの目的
  要件
  品質属性
  構成要素の責務
  構成要素が担当しない範囲
  接続関係
  情報の流れ
  信頼境界
  権限境界の構造
  modelの配置
  検索機構の配置
  記憶機構の配置
  toolの配置
  agentの配置
  policy層の配置
  評価層の配置
  観測・記録機構の配置
  人間確認点の配置
  障害伝播の設計
  影響範囲の設計
  fallback / containment の設計
  配置構成
  移行・置換計画
  実行時の整合主張
  構造判断の履歴
```

### 18.3 扱わないもの

AIAGDは、Agentic AIの実行、tool呼び出しの実行管理、判断権限、承認、責任主体の割当、AI安全上の危険判定、運用実行、障害対応、実装品質、開発相談、成果物構成、GD横断の振り分けを扱わない。

AIAGDが構造を確認することは、実行管理、権限付与、安全判定、運用成功、実装品質の保証を意味しない。

---

## 19. SEGD

### 19.1 基本情報

```text id="segd_basic_info"
略称:
  SEGD

正式名称:
  Software Engineering Governance Definition

配置先:
  definitions/domain_extensions/ordinary/segd_v0.1.0_en.json
```

### 19.2 役割

SEGD は、software engineeringの実行、検証、変更管理、成果物の識別、修復、巻き戻し、再実行、実装履歴を扱うGDである。

```text id="segd_scope"
SEGDが見るもの:
  要件
  受け入れ条件
  仕様
  設計と実装の対応
  repository
  branch
  base revision
  source codeの変更
  設定変更
  dependencyの変更
  migrationの変更
  静的検証
  unit testの結果
  integration testの結果
  regression testの結果
  build結果
  成果物の識別
  deployment準備状態
  deployment結果
  修復
  rollbackの範囲
  rerunの範囲
  実装判断の履歴
```

### 19.3 扱わないもの

SEGDは、開発相談、AI構造設計、通常のAgentic AI実行、継続運用、判断権限、AIを介した安全上の危険、プロジェクト進行整理、成果物公開品質を扱わない。

SEGDが検証状態を確認することは、実行許可や運用成功の保証ではない。  
生成されたcodeは、検証なしに正しいとは扱わない。build成功は実行時の正しさを意味せず、  
unit test成功は結合時の正しさを意味しない。deployment完了は運用成功を意味しない。

---

## 20. OMRGD

### 20.1 基本情報

```text id="omrgd_basic_info"
略称:
  OMRGD

正式名称:
  Operations, Maintenance, and Reliability Governance Definition

配置先:
  definitions/domain_extensions/ordinary/omrgd_v0.1.0_en.json
```

### 20.2 役割

OMRGD は、運用状態、保守性、復旧可能性、信頼性を扱うGDである。

```text id="omrgd_scope"
OMRGDが見るもの:
  運用状態
  serviceの健全性
  監視対象
  log
  指標
  alert
  incident
  failure
  degradation
  outage
  runbook
  rollback手順
  recovery手順
  保守作業
  運用上の危険
  変更影響
  service level
  信頼性目標
  error budget
  dependencyの健全性
  運用負荷
  技術的負債
  保守時間帯
  escalation path
  incident後のreview
  再発防止
  継続的改善項目
  運用上の引き渡し
```

### 20.3 扱わないもの

OMRGDは、新規開発、実装そのもの、プロジェクト管理全体、戦略判断、成果物構成、正式な法的判断、組織承認を扱わない。

OMRGDが運用状態を見ることは、運用成功や復旧完了を自動的に保証するものではない。  
動いていることは信頼できる運用状態を意味しない。alertが出ていないことは健全性を意味しない。  
復旧を試したことは復旧完了を意味しない。incidentを閉じたことは再発防止を意味しない。

---

## 21. まとめ

本prototypeの16個のGDは、次のように分担する。

```text id="e2d457"
CDOGD:
  横断的にrouting、scope調整、handoff、repair propagation を扱う

SPPGD:
  戦略判断の構造を整理する

DAAGD:
  MARGD内で authority / accountability 判断を担当する
  自律判断として扱えるか、人間判断へ戻すべきか、承認待ちか、委任範囲外か、責任主体未確定かを判断する

SDAGD:
  SPPGDの判断構造と、DAAGDが判断した authority / accountability state を監査する
  DAAGDを代替しない

SDMRGD:
  SDAGDの監査状態をメタレビューする

ordinary系GD:
  専門的意見・判断材料・確認条件・危険の指摘・修復候補・引き渡し材料を出す
  それ自体はMARGD内の authority / accountability 判断ではない
```

ordinary系GDは、実行許可、最終決定、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態を判断するGDではない。  
ordinary系GDの出力は、SPPGDにおける戦略判断構造の材料、またはDAAGDにおける authority / accountability 判断の入力や参照材料にはなりうる。

しかし、それ自体は戦略判断構造そのものでも、MARGD内の authority / accountability 判断そのものでもない。  
MARGD内で authority / accountability 判断を行うのはDAAGDである。

MARGDおよび各GDの利用上の注意と限界は、`usage_and_limitations_ja.md` を参照すること。