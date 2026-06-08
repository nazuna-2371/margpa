
---

# ARGD と DAGD の技術概要

---

## 1. 本資料の位置づけ

本資料は、MARGD family の主要構成である ARGD と DAGD について、役割、構造、併用時の関係、想定用途、制約を説明する技術概要である。

本資料は、ARGD / DAGD の全文リファレンスではない。  
各定義の全文は、以下の JSON ファイルを参照する。

```text
definitions/
  argd_v0.3.0_en.json
  argd_v0.3.0_ja.json
  argd_v0.3.1_en.json
  argd_v0.3.1_ja.json
  dagd_v0.4.4_en.json
  dagd_v0.4.4_ja.json
  argd_v0.3.0_en_dagd_v0.4.4_en.json
  argd_v0.3.0_ja_dagd_v0.4.4_ja.json
  argd_v0.3.1_en_dagd_v0.4.4_en.json
  argd_v0.3.1_ja_dagd_v0.4.4_ja.json
````

本資料の目的は、ARGD / DAGD を初めて読む人が、以下を理解できるようにすることである。

* ARGD は何を統治する定義なのか
* DAGD は何を統治する定義なのか
* 両者はなぜ別々に存在するのか
* 併用すると何が補完されるのか
* どのような用途に向いているのか
* どのような限界があるのか

---

## 2. 前提となる用語

### 2.1 MARGD

MARGD は、Modular AI Runtime Governance Definition の略である。

日本語では、モジュール型AIランタイム統治定義と呼ぶ。

MARGD は単一の定義ではなく、ARGD、DAGD、将来的な追加定義を含む runtime governance definition の family 名である。

```text
MARGD
= Modular AI Runtime Governance Definition
= モジュール型AIランタイム統治定義
= MARGPA 配下で使われる統治定義群 / 構文群の上位カテゴリ
```

### 2.2 ARGD

ARGD は、Axiomatic Reasoning Governance Definition の略である。

日本語では、公理型推論統治定義と呼ぶ。

ARGD は、AI / LLM の推論手続、入力解釈、文脈優先、前提固定、矛盾処理、情報不足処理、反証、分岐、回答構造、表現制御、自己修復を扱う runtime governance definition である。

```text
ARGD
= Axiomatic Reasoning Governance Definition
= 公理型推論統治定義
= 推論手続を統治する runtime governance definition
```

ARGD は、通称として Dialogue Axiom / 対話公理 を持つ。

### 2.3 DAGD

DAGD は、Declarative AI Governance Definition の略である。

日本語では、宣言型AI統治定義と呼ぶ。

DAGD は、AI / LLM の目的、禁止挙動、要求挙動、能力要件、評価、修復、活性化、自己監査、監査結果から行動への対応、状態報告を扱う runtime governance definition である。

```text
DAGD
= Declarative AI Governance Definition
= 宣言型AI統治定義
= 挙動・制約・評価・修復・監査・再拘束などを扱う宣言型統治定義
```

### 2.4 runtime governance specification

本リポジトリでいう runtime governance specification とは、AI / LLM の実行時に外部から与える統治仕様を指す。

これは、モデル重み、学習データ、組み込み安全層を変更するものではない。

また、AI / LLM の内部推論を直接覗くものでも、書き換えるものでもない。

対象は、出力として観測可能な応答生成挙動である。

![MARGPA Dense Research Architecture](assets/images/margpa_architecture_dense_research_ja.png)

---

## 3. ARGD と DAGD の最短比較

ARGD と DAGD は、同じ役割を持つ構文ではない。

最短で分けると、次のようになる。

| 項目   | ARGD                          | DAGD                              |
| ---- | ----------------------------- | --------------------------------- |
| 主対象  | 推論手続                          | 宣言仕様・挙動統治                         |
| 主な役割 | どのように解釈し、推論し、回答するかを統治する       | 何を目標とし、何を禁じ、何を要求し、どう評価・修復するかを定義する |
| 近い層  | procedural / how layer        | declarative / what layer          |
| 主な対象 | 入力解釈、前提固定、分岐、反証、回答構造、自己修復     | 目的、禁止事項、要求挙動、評価、修復、活性化、状態報告       |
| 強み   | 文脈保持、前提保持、反証、分岐保持、論理整合性       | 方針固定、挙動制約、監査、修復、再拘束、状態報告          |
| 単独使用 | 可能                            | 可能                                |
| 併用   | DAGD の目的・制約を、ARGD が推論手続側から支える | ARGD の推論手続に、目的・評価・修復条件を与える        |

簡略化すると次の通りである。

```text
ARGD:
どのように考え、保持し、分岐し、回答を作るか

DAGD:
何を目標にし、何を避け、何を評価し、どう修復するか
```

---

## 4. ARGD の役割

ARGD は、AI / LLM の推論手続と回答形成を統治するための定義である。

通常のプロンプトが「何をしてほしいか」を依頼するのに対し、ARGD は「入力や文脈をどう扱い、どの順序で推論し、どのように回答へ反映するか」を指定する。

ARGD が扱う主な領域は次の通りである。

```text
- 入力解釈
- 文脈優先順位
- 定義
- 前提固定
- 矛盾処理
- 情報不足処理
- 反証
- 複数仮説の分岐保持
- 回答構造
- 表現制御
- 対話効率
- 自己修復
```

ARGD の目的は、AI / LLM に新しい知識を与えることではない。

目的は、既に与えられた情報、前提、文脈、ユーザー指示を、失われにくく、混ざりにくく、過度に一般化されにくい形で扱わせることである。

---

## 5. ARGD の主要構造

ARGD v0.3.1 では、主に以下の6区分で推論手続を統治する。

```text
1. intp_interpretive_premises
2. ctxp_context_priority
3. info_contradiction_information
4. qual_reasoning_quality
5. form_structural_expression
6. repr_efficiency_repair
```

各区分の役割は次の通りである。

| 区分                             | 役割                                |
| ------------------------------ | --------------------------------- |
| intp_interpretive_premises     | 入力解釈、対象範囲、評価軸、前提保持を扱う             |
| ctxp_context_priority          | 文脈優先順位、決定事項、役割分離、主題切替を扱う          |
| info_contradiction_information | 矛盾、情報不足、複数仮説、暫定前提を扱う              |
| qual_reasoning_quality         | 非迎合、反証、根拠、論理整合性、事実・推論・仮定・評価の分離を扱う |
| form_structural_expression     | 回答構造、表現精度、分岐、長文時の構成を扱う            |
| repr_efficiency_repair         | ドリフト検出、修復、再固定、効率性を扱う              |

---

## 6. ARGD の重要タグ

ARGD には、いくつかの重要タグがある。

ここでは、公開版を理解するうえで特に重要なものを説明する。

### 6.1 KEEP

KEEP は、ユーザー入力や過去ログの構造を勝手に圧縮・要約・再解釈しないための指示である。

特に、研究、設計、仕様、実装、複数論点を扱う場合に重要である。

```text
KEEP:
入力や過去ログを無断で圧縮・要約・再解釈せず、
構造、論点順序、分岐、優先順位を保持する。
```

### 6.2 FIXD

FIXD は、確定済みの定義、名称、構成、順序、役割分離、優先順位を、明示的変更まで固定するための指示である。

長い対話で、前に決めたことが薄れたり、別の提案で上書きされたりすることを抑える。

```text
FIXD:
確定済みの定義・構成・役割・優先順位を、
明示的変更まで固定する。
```

### 6.3 ANTI

ANTI は、同意先行や迎合を抑えるための指示である。

ユーザーの主張に対して、無批判に肯定するのではなく、反証、弱点、代替案を検討した後に採用・同意することを求める。

```text
ANTI:
反証、弱点、代替案を検討する前の同意を抑制する。
```

### 6.4 FALS

FALS は、反証可能性、対抗仮説、破綻条件、代替解釈を能動的に確認するための指示である。

ARGD v0.3.1 で特に強化された要素である。

```text
FALS:
提案、主張、前提、結論に対して、
反証可能性、対抗仮説、破綻条件、代替解釈を検討する。
```

### 6.5 LEAD

LEAD は、反証、再検討、代替解釈、採用保留を示すときに、短い導入文を自然に出すための指示である。

反証ブロックへの遷移を明確にするためのタグである。

```text
LEAD:
反証や再検討に入るとき、短い導入文を出す。
```

### 6.6 TONE

TONE は、反証導入文が攻撃的、人格評価的、感情的にならないようにするための指示である。

反証を行うが、不要に対立的な表現へ寄せない。

```text
TONE:
反証導入文を、非攻撃的・簡潔・内容依存に保つ。
```

### 6.7 REPR

REPR は、ズレ、ドリフト、誤り、矛盾を検出したとき、修正内容と再固定内容を明示して即時修復するための指示である。

長大対話では特に重要である。

```text
REPR:
逸脱、ドリフト、誤り、矛盾を検出した場合、
何が誤りで、何を修正し、何を再固定するかを明示する。
```

---

## 7. ARGD v0.3.0 と v0.3.1

本リポジトリでは、ARGD v0.3.0 と ARGD v0.3.1 を置く。

```text
definitions/
  argd_v0.3.0_en.json
  argd_v0.3.0_ja.json
  argd_v0.3.1_en.json
  argd_v0.3.1_ja.json
```

どちらも、ライトユーザー向けの軽量Promptではなく、研究、設計、検証、精密作業向けの基盤仕様である。

大きな違いは、v0.3.1 では反証・非迎合・代替解釈の扱いが強化されている点である。

| 版           | 位置づけ                | 主な特徴                                          |
| ----------- | ------------------- | --------------------------------------------- |
| ARGD v0.3.0 | 研究・設計・検証向けの基盤仕様     | 推論手続、文脈保持、前提固定、構造化を扱う                         |
| ARGD v0.3.1 | v0.3.0 を基に反証系を強化した版 | ANTI / FALS / LEAD / TONE により、反証・非迎合・代替解釈を強める |

注意点として、v0.3.1 は反証や非迎合を強めるため、出力がやや重くなる場合がある。

そのため、用途によっては v0.3.0 の方が扱いやすい場合もある。

ただし、どちらも現時点では精密作業向けの基盤仕様であり、日常会話向けの軽量版ではない。

---

## 8. DAGD の役割

DAGD は、AI / LLM の挙動方針を宣言的に定義するための仕様である。

ARGD が「どのように扱うか」を支えるのに対し、DAGD は「何を目標とし、何を禁じ、何を要求し、どのように評価・修復するか」を扱う。

DAGD が扱う主な領域は次の通りである。

```text
- policy_goal
- constraints
- capabilities
- evaluation
- repair
- activation
- self_audit
- audit_to_action
- status_reporting
```

DAGD は、AI / LLM の挙動を完全に保証するものではない。

DAGD の役割は、実行時の外部指示として、目的、禁止事項、要求挙動、評価基準、修復手順、状態報告の構造を明示することである。

---

## 9. DAGD の主要構造

DAGD v0.4.4 の主要構造は次の通りである。

| 区分               | 役割                                   |
| ---------------- | ------------------------------------ |
| policy_goal      | 目標となる統治方針を定義する                       |
| constraints      | 禁止挙動、要求挙動、実行時ルールを定義する                |
| capabilities     | 要求能力・望ましい能力・能力分類を定義する                |
| evaluation       | 監査対象、成功シグナル、ドリフトシグナル、スコアリング、重大度を定義する |
| repair           | 誤り、矛盾、情報不足、ドリフト発生時の修復行動を定義する         |
| activation       | 初期化、再拘束、再固定、活性化キー、状態遷移を定義する          |
| self_audit       | 応答前後の自己監査条件を定義する                     |
| audit_to_action  | 監査結果を修復・再拘束・状態報告へ接続する規則を定義する         |
| status_reporting | 状態報告の条件と表示項目を定義する                    |

---

## 10. DAGD の policy_goal

DAGD v0.4.4 の policy_goal は、主に次のような方向を持つ。

```text
- truthfulness
- reasoning_integrity
- non_sycophantic_behavior
- transparent_reasoning
- context_preservation
- premise_preservation
- auditability
- repairability
```

これらは、DAGD が目指す統治方針である。

ただし、これらの目標を指定しても、AI / LLM が常に完全に達成するわけではない。

あくまで、実行時の外部仕様として、応答生成時に優先すべき方向を明示するものである。

---

## 11. DAGD の constraints

constraints は、DAGD の中でも中心的な構造である。

主に次の3種類を含む。

```text
1. prohibited_behaviors
2. required_behaviors
3. runtime_rules
```

### 11.1 prohibited_behaviors

prohibited_behaviors は、避けるべき挙動を分類する。

例として、次のようなものが含まれる。

* hallucination
* unsupported assertion
* false certainty under insufficient information
* sycophancy
* unauthorized average-case substitution
* premise drift
* context mixing
* hypothesis collapse
* assumption hiding
* unapproved summarization
* unsupported vagueness
* detected error without repair

これらは、MARGD が特に避けたい失敗モードである。

### 11.2 required_behaviors

required_behaviors は、求める挙動を分類する。

例として、次のようなものが含まれる。

* 入力構造の保持
* 確定済み文脈の保持
* 対象範囲の定義
* 評価軸の明示
* 前提保持
* 矛盾時の停止
* 事実・推論・仮定・評価の分離
* 根拠の開示
* 不確実性の開示
* 複数仮説の分岐保持
* 修復と再固定
* 状態劣化時の報告

### 11.3 runtime_rules

runtime_rules は、実行時に守るべき優先順位や適用範囲を定義する。

主な優先順位は次の通りである。

```text
1. 最新の明示的ユーザー指示
2. 現在の対話内で確定した定義・前提・決定事項
3. 文脈からの合理的推定
4. 一般的慣行
```

この優先順位は、長い対話で特に重要である。

一般論や内部最適化によって、ユーザーが明示した決定事項が上書きされることを避けるためである。

---

## 12. DAGD の evaluation

evaluation は、DAGD が何を監査対象とするかを定義する。

主な監査対象には、次のようなものが含まれる。

```text
- input_structure_preservation
- context_preservation
- premise_preservation
- scope_definition
- instruction_priority_compliance
- contradiction_handling
- fact_inference_separation
- hypothesis_branch_preservation
- information_loss
- evidence_basis_disclosure
- traceability_disclosure
- confidence_basis_disclosure
- uncertainty_disclosure
- vagueness_control
- dialog_efficiency
- self_repair_execution
- topic_boundary_preservation
- decision_fixity_preservation
- evaluation_basis_disclosure
```

DAGD は、これらの観点を使って、応答がどのようにズレたか、どの次元が弱いか、どの修復が必要かを扱う。

この評価構造は、MARGD を単なる「良い応答をしてください」という依頼文ではなく、監査可能な runtime governance specification として扱うために重要である。

---

## 13. DAGD の repair

repair は、誤り、矛盾、情報不足、ドリフトが発生したときの修復行動を扱う。

DAGD v0.4.4 では、主に次のような状態を修復対象とする。

```text
- detected_drift
- detected_contradiction_in_response
- detected_premise_drift
- detected_context_mixing
- detected_unapproved_summarization
- detected_evaluation_without_basis
- detected_confidence_without_basis
- detected_false_certainty_under_insufficient_information
- detected_evidence_basis_omission_for_load_bearing_claim
- detected_traceability_omission_for_load_bearing_claim
- detected_uncertainty_suppression_under_insufficient_information
- user_reported_governance_failure
- audit_score_below_threshold
- critical_severity_detected
```

修復時には、単に謝罪するのではなく、次のような処理が求められる。

* 誤りの種類を特定する
* 重大度を分類する
* 影響を受けた主張や箇所を特定する
* 何が誤っていたかを明示する
* 根拠、トレーサビリティ、確信度、不確実性のどこに問題があったかを分ける
* unsupported な主張を撤回、修正、または再限定する
* 修復対象を明示する
* 再固定対象を明示する
* 修復後の統治状態で続行する

この構造により、DAGD は「誤ったら謝る」ではなく、「何がどうズレたかを分解し、修復し、再固定する」ことを目指す。

---

## 14. DAGD の activation

activation は、DAGD の有効化、再拘束、再固定、再初期化を扱う。

DAGD v0.4.4 では、次のような activation key が定義されている。

```text
- compact_reactivation_signal
- run
- activate
- rebind
- enforce
- reinitialize
- full_dagd_reinjection
- user_requested_re_fix
- audit_failure_reactivation
```

各キーの意味は異なる。

| キー                         | 役割                                |
| -------------------------- | --------------------------------- |
| activate                   | 非アクティブまたは不確実な状態から有効化する            |
| run                        | 現在の DAGD を現在の応答生成に適用する            |
| rebind                     | ドリフトやスコープぼけの後に、現在の応答とスレッドを再アンカーする |
| enforce                    | 統治強度を上げる                          |
| reinitialize               | 現在の DAGD のもとで再拘束・再固定する            |
| full_dagd_reinjection      | 新しい DAGD 全文を権威ある定義として再投入する        |
| user_requested_re_fix      | ユーザーが報告した統治失敗に対して、明示的に修復・再固定する    |
| audit_failure_reactivation | 監査で失敗や不安定性が検出された場合に、再活性化経路を提示する   |

これにより、DAGD は単なる初期化用仕様ではなく、長い対話の途中で再固定・再拘束するための構造を持つ。

---

## 15. DAGD の self_audit と audit_to_action

self_audit は、応答前後の自己監査を扱う。

DAGD v0.4.4 では、通常は lightweight audit を行い、高複雑度、多主題、ドリフト検出、ユーザー報告、長文脈不安定性などがある場合に full audit を選択する構造になっている。

audit_to_action は、監査結果を実際の行動へ変換する規則である。

例として、次のような対応がある。

```text
低重大度:
必要に応じてインライン修復

中重大度:
修復と再固定

高重大度:
明示的修復通知、状態報告、再拘束

重大:
明示的修復通知、劣化状態報告、再初期化、必要に応じて再投入推奨
```

この構造により、DAGD は単に「自己監査してください」と言うだけではなく、監査結果を修復、再固定、状態報告へ接続する。

---

## 16. DAGD の status_reporting

status_reporting は、DAGD に明示的に組み込まれている機能である。

状態報告は、MARGD 適用時に偶然出る副次的挙動ではなく、DAGD の設計上の構成要素である。

DAGD v0.4.4 では、主に次のような状態報告モードを持つ。

```text
- silent_by_default
- emit_on_anomaly
- emit_on_user_request
```

つまり、通常は状態報告を過剰に出さず、異常時やユーザー要求時に出すことを想定している。

状態報告で扱い得る項目には、次のようなものがある。

```text
- governance_state
- detected_deviations
- severity
- evidence_basis_status
- traceability_status
- confidence_basis_status
- uncertainty_disclosure_status
- repair_applied
- re_fix_applied
- reinjection_recommended
```

状態報告の価値は、長大対話や複雑作業で、現在の前提、修復状況、再固定状態、未解決事項を確認できる点にある。

一方で、状態報告には課題もある。

* 表示量が多くなりやすい
* 本文と状態報告が混ざる可能性がある
* モデルによって粒度が揺れる
* 軽量タスクでは冗長に見える
* 発火条件を調整する必要がある

したがって、状態報告は不要な副作用ではなく、DAGD の機能である。
ただし、表示条件、表示量、表示位置、本文との分離方法は今後の調整対象である。

---

## 17. ARGD と DAGD の併用時の流れ

ARGD と DAGD を併用する場合、基本的には次のような流れになる。

```text
1. ARGD を投入する
2. DAGD を投入する
3. スレッドの目的・対象範囲・作業方針を設定する
4. 必要に応じて、対象ドメインやタスク固有の条件を追加する
5. 長い対話の途中でズレた場合は、再固定・再拘束・修復を行う
```

実際の最小イメージは次の通りである。

```text
1. まず、ARGDで初期化。
2. 続いて、DAGDで初期化。
3. このスレッドの目的、対象範囲、保持すべき前提、作業方針を明示する。
```

ARGD は推論手続側の土台を整える。
DAGD は目標、制約、監査、修復、状態報告の土台を整える。
最後に、スレッド固有の目的設定を行う。

この3段階により、汎用定義と現在タスク固有の目的を分けて扱いやすくなる。

---

## 18. 併用時に期待される挙動

ARGD + DAGD を併用すると、次のような挙動へ寄せやすくなる可能性がある。

| 観点    | 期待される挙動                       |
| ----- | ----------------------------- |
| 文脈保持  | 初期に共有した目的、前提、決定事項を保持しやすくなる    |
| 前提固定  | 変更済み事項と未変更事項を分けやすくなる          |
| 情報不足  | 未確認情報、結論への影響、暫定前提を明示しやすくなる    |
| 根拠分離  | 直接根拠、推論、仮説、不明点を分けやすくなる        |
| 非迎合   | ユーザーの誘導や希望に対し、反証や確認を挟みやすくなる   |
| 複数仮説  | 単一結論へ早期収束せず、複数候補を保持しやすくなる     |
| 自己監査  | 前回応答の断定しすぎ、根拠不足、前提逸脱を点検しやすくなる |
| 修復    | 誤り検出後に、修正内容と再固定内容を明示しやすくなる    |
| 状態報告  | 長い対話で、現在の統治状態や未解決事項を確認しやすくなる  |
| 監査可能性 | 判断根拠、未確認事項、修復履歴を追いやすくなる       |

ただし、これは保証ではない。

実際の効果は、使用する AI / LLM の能力、文脈長、指示追従性、タスク内容、投入形式、ユーザー入力の明確さに依存する。

---

## 19. 単独使用する場合

ARGD と DAGD は、必ず併用しなければならないものではない。

### 19.1 ARGD のみが向く場合

ARGD のみは、主に推論手続、文脈保持、前提固定、反証、分岐保持を強めたい場合に向く。

例：

* 研究議論
* 仕様設計
* 複雑な要件整理
* 長文レビュー
* 論点分解
* 反証重視の議論
* 前提保持が重要な相談

ただし、ARGD のみでは、DAGD が持つ評価、修復、活性化、状態報告の構造は弱くなる。

### 19.2 DAGD のみが向く場合

DAGD のみは、目的、禁止挙動、要求挙動、評価、修復、状態報告を明示したい場合に向く。

例：

* AI運用方針の明示
* 禁止挙動の固定
* 監査観点の設定
* 修復条件の設定
* 状態報告の運用
* Agentic AI の権限境界管理

ただし、DAGD のみでは、ARGD が持つ細かい推論手続、反証導入、入力構造保持、前提分岐の統治は弱くなる。

### 19.3 ARGD + DAGD が向く場合

ARGD + DAGD の併用は、長文、精密作業、複雑文脈、高リスク領域、監査可能性が必要な場面に向く。

例：

* 長大な研究・設計対話
* RAG / 社内ナレッジAI
* 法務・規程・監査文書補助
* 医療補助AIの情報整理
* 教育AIの学習支援
* Agentic AI の権限・目的・状態管理
* 複数ターンにわたる検証・修復作業

---

## 20. 向いているタスク

ARGD / DAGD は、次のようなタスクに向いている。

```text
- 前提保持が重要なタスク
- 文脈混線を避けたいタスク
- 断定しすぎを避けたいタスク
- 根拠と推論を分けたいタスク
- 複数仮説を保持したいタスク
- ユーザーの誘導や迎合を抑えたいタスク
- 誤り検出後の修復が重要なタスク
- 長文・複雑文脈の作業
- 監査可能な出力が必要な作業
- 研究、設計、検証、レビュー系の作業
```

代表例は次の通りである。

```text
- 研究議論
- 仕様設計
- コードレビュー
- 設計レビュー
- RAG / ナレッジ回答
- 社内規程確認
- 法務・監査補助
- 医療補助AI
- 教育AI
- Agentic AI
```

---

## 21. 向いていないタスク

ARGD / DAGD は、すべての会話に向いているわけではない。

次のような用途では過剰になりやすい。

```text
- 雑談
- 軽い質問
- 短い文章生成
- 大まかな感想交換
- 広い発想出し
- 制約を緩めたい創作
- ざっくりした相談
- ユーザー側の目的や前提が曖昧なままの会話
```

理由は、ARGD / DAGD が探索空間を狭め、前提保持、根拠管理、不確実性開示、反証、監査、修復を強める方向に設計されているためである。

そのため、軽い会話では次のように感じられる場合がある。

* 出力が長い
* 留保が多い
* 確認が多い
* 反証が多い
* 状態報告が重い
* 自由な補完が少ない

これは単なる欠点ではなく、用途依存の性質である。

研究、設計、精密作業では長所になり得るが、雑談や軽作業では過剰になり得る。

---

## 22. ドメイン特化の必要性

ARGD / DAGD は、特定ドメインに最適化済みの完成品ではない。

現時点では、精密作業、長文文脈、前提保持、監査、修復のための基盤仕様である。

実務適用する場合は、対象ドメインに応じて、次のような要素を追加する必要がある。

```text
- 業務要件
- 対象ユーザー
- リスク分類
- 評価軸
- 禁止事項
- 根拠提示要件
- 人間確認条件
- 専門家レビュー条件
- 権限管理
- 監査ログ
- 外部安全機構
- 法令・規約・安全基準への適合確認
```

たとえば、医療補助AI、教育AI、Agentic AI では、必要な派生条件が異なる。

そのため、ARGD / DAGD はそのまま全用途へ投入する完成品ではなく、用途別・ドメイン別に派生させるための基盤仕様として扱う。

---

## 23. モデル要件

ARGD / DAGD は、十分な能力を持つ AI / LLM での利用を前提とする。

特に重要なのは次の能力である。

```text
- 長文コンテキスト保持力
- 長文指示追従能力
- 圧縮・再展開能力
- 推論力
- 出力構造化能力
- 自己監査に近い応答生成能力
- 修復指示への追従能力
```

軽量モデル、高速応答向けモデル、短文応答向けモデル、長文コンテキスト保持が弱いモデルでは、次のような問題が起こり得る。

* ARGD / DAGD 自体を保持できない
* 初期指示が途中で薄れる
* 前提固定が効かない
* 自己監査が浅くなる
* 修復や再固定が不安定になる
* 状態報告が過剰または不十分になる

したがって、ARGD / DAGD の有効性は、モデル性能、実装環境、文脈長、タスク内容に強く依存する。

---

## 24. 非保証事項

ARGD / DAGD は、以下を保証しない。

```text
- 正確性
- 安全性
- 法令適合
- 規格適合
- 専門判断の妥当性
- 本番運用可能性
- すべてのモデルでの同等効果
- すべてのタスクでの有効性
- 完全な前提保持
- 完全なドリフト防止
- 完全な自己修復
```

また、以下を行うものでもない。

```text
- モデル重みの変更
- 学習データの変更
- 組み込みシステムポリシーの上書き
- 安全層の回避
- jailbreak
- 内部推論の直接閲覧
- 内部推論の直接書き換え
- モデル基礎性能の向上
```

ARGD / DAGD は、inference-time external governance specification である。

つまり、推論時に外部から与える統治仕様であり、モデル本体そのものを変更するものではない。

---

## 25. 公開版としての現時点の位置づけ

本リポジトリで公開する ARGD / DAGD は、実験的な基盤仕様である。

現時点の位置づけは次の通りである。

```text
ARGD / DAGD は、特定ドメインに最適化済みの完成品ではない。

精密な AI / LLM 運用、評価、監査、修復を行うための基盤仕様である。

実務適用時には、対象ドメインの業務要件、リスク、評価軸、根拠提示要件、

人間確認条件などを追加し、ドメイン特化版へ派生させることを前提とする。
```

短く言えば、ARGD / DAGD は万能会話Promptではない。

精密作業、長文文脈、前提保持、根拠管理、監査、修復を重視する AI / LLM workflow のための runtime governance foundation である。

---

## 26. 次に読む文書

ARGD / DAGD の使い方を知りたい場合は、次を読む。

```text
docs/quickstart_ja.md
```

利用原則、向いている用途、制約、非保証事項を確認したい場合は、次を読む。

```text
docs/usage_and_limitations_ja.md
```

小規模検証と長大コンテキスト運用観察を確認したい場合は、次を読む。

```text
docs/validation_and_operation_observation_ja.md
```

応用可能性を確認したい場合は、次を読む。

```text
docs/use_cases_ja.md
docs/use_cases/medical_assistive_ai_ja.md
docs/use_cases/education_ai_ja.md
docs/use_cases/agentic_ai_ja.md
docs/use_cases/common_behavior_patterns_ja.md
```

定義本体を確認したい場合は、次を読む。

```text
definitions/
  argd_v0.3.0_en.json
  argd_v0.3.0_ja.json
  argd_v0.3.1_en.json
  argd_v0.3.1_ja.json
  dagd_v0.4.4_en.json
  dagd_v0.4.4_ja.json
  argd_v0.3.0_en_dagd_v0.4.4_en.json
  argd_v0.3.0_ja_dagd_v0.4.4_ja.json
  argd_v0.3.1_en_dagd_v0.4.4_en.json
  argd_v0.3.1_ja_dagd_v0.4.4_ja.json
```

---

ARGD / DAGD は、AI / LLM を万能化するための構文ではなく、長文文脈、前提保持、根拠管理、自己監査、修復、状態報告を扱いやすくするための外部統治仕様である。

本資料はその技術的な入口であり、実際の利用時には `docs/quickstart_ja.md`、制約確認には `docs/usage_and_limitations_ja.md`、検証観察には `docs/validation_and_operation_observation_ja.md` を参照する。

---
