# Architecture

この文書では、MARGD Runtime Governance Bundle Prototype の概念構造を説明する。

ここで扱うarchitectureとは、repository上のディレクトリ構造ではなく、  
ARGD / DAGD、CDOGD、bundle、domain extensions、templates がどのような責務分離で接続されるかを指す。

---

## 1. 全体像

MARGD Runtime Governance Bundle は、複数のgovernance componentを1つのruntime governance構造として束ねるための枠組みである。

本prototypeでは、次の層に分けて考える。

```text id="i02s6q"
core governance:
  ARGD
  DAGD

orchestration governance:
  CDOGD

registered domain extensions:
  decision pipeline domain extensions
  conditional watchdog domain extensions
  ordinary domain extensions

bundle:
  これらをまとめるruntime governance container
```

ARGD / DAGD は、reasoning と behavior governance の基盤である。  
CDOGD は、複数domainを横断して routing、scope調整、handoff、repair propagation を扱う orchestration governance である。  
registered domain extensions は、それぞれの専門領域や工程に応じたgovernance scopeを扱う。

bundle は、これらをまとめるためのruntime governance containerである。  
bundle自体は、専門判断、authority / accountability 判断、監査、承認、実行許可、最終決定を行わない。

---

## 2. core governance

core governance は、各domain extensionが前提とする基盤である。

```text id="blhmyb"
ARGD:
  reasoning procedure governance

DAGD:
  behavior / audit / repair / activation / status governance
```

ARGD は、入力解釈、前提整理、定義固定、矛盾処理、不足情報処理、分岐、反証、回答構成、自己修復など、reasoning procedure の基盤を担う。

DAGD は、目的、制約、能力、評価、修復、再活性化、自己監査、状態報告など、behavior governance の基盤を担う。

本prototypeでは、ARGD / DAGD の詳細は扱わない。  
ARGD / DAGD の詳細は、repository root側のREADMEおよび既存資料を参照すること。

---

## 3. bundle

bundle は、core governance、orchestration governance、registered domain extensions をまとめるruntime governance containerである。

bundle自体は、専門判断を行わない。  
また、bundle自体がdomainの優先順位、起動順、判断権限、承認権限、責任主体を固定するものでもない。

```text id="xyxpzn"
bundleが担うもの:
  core governance を参照する
  orchestration governance を含める
  registered domain extensions を格納する
  componentをruntime governance bundleとして束ねる

bundleが担わないもの:
  専門判断
  authority / accountability 判断
  監査
  最終決定
  承認
  実行許可
  責任主体の割当
  domain priorityの固定
  domain activationの自動発生
```

重要なのは、bundleに登録されていることと、実際に起動していることは同じではない、という点である。

```text id="umuegv"
loaded != active
registered != active
reference != governance
registration != activation
```

bundleは、componentを置くための器である。  
実際にどのdomainをどの範囲で扱うか、どの役割で適用するか、どこで引き渡すかは、CDOGD、runtime context、登録情報、適用根拠によって整理される。

---

## 4. CDOGD

CDOGD は、Cross-Domain Orchestration Governance Definition である。

CDOGDの役割は、複数のregistered domain extensionsを横断して、どのGDをどの範囲で扱うか、どの役割で適用するか、どこで引き渡すかをまとめることである。

```text id="foj1u6"
CDOGDが扱うもの:
  domain候補
  適用範囲
  function role
  domain間の重なり
  抑制・弱化
  引き渡し
  修復の伝播
```

CDOGDは、domain名だけでroutingするものではない。  
また、固定された優先順位表や、固定されたdomain owner表によって処理を決めるものでもない。

CDOGDは、task、対象、必要なgovernance、registered manifest、capability、role、非対象条件、根拠、runtime contextなどをもとに、domain間の適用範囲と引き渡しを整理する。

ただし、CDOGDは最終決定を行わない。  
DAAGDの authority / accountability 判断、SDAGDの主監査、SDMRGDのメタレビュー、ordinary domain extensions の専門処理を代替しない。

```text id="9rqgff"
CDOGD:
  まとめる

CDOGD does not:
  最終決定する
  承認する
  実行許可を出す
  責任主体を割り当てる
  authority / accountability 判断を代替する
  専門判断を代替する
  主監査を代替する
```

CDOGDの詳細は、`routing_principles_ja.md` を参照すること。

---

## 5. registered domain extensions

registered domain extensions は、bundleに登録されるdomain-specificなGD群である。

本prototypeでは、15個のregistered domain extensionsを持つ。

```text id="dyxp4m"
decision pipeline domain extensions:
  SPPGD
  DAAGD
  SDAGD

conditional watchdog domain extensions:
  SDMRGD

ordinary domain extensions:
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

これらの分類は、domain extensionの性質を整理するためのものである。  
分類順や記載順は、起動順、優先度、権限の強さを意味しない。

登録されているdomain extensionは、常に起動しているわけではない。  
また、登録されていることは、そのGDが最終判断、承認、実行許可、責任主体の確定を行うことを意味しない。

---

## 6. decision pipeline

decision pipeline domain extensions は、専門材料、戦略判断構造、authority / accountability 判断、監査を分離するためのGD群である。

```text id="c1s8oy"
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

SPPGD は、目的、前提、制約、選択肢、優先順位、継続、停止、撤退、保留、再評価条件などを整理する。  
SPPGDは、戦略判断の構造を作るが、authority / accountability 判断は行わない。

DAAGD は、既存のsystem policy、developer policy、runtime policy、tool権限、外部実行権限、委任条件、承認条件、責任分界に基づき、MARGD内の authority / accountability state を判断する。  
DAAGDは、当該出力・判断候補・実行候補をAIまたはruntimeの自律判断として扱えるか、人間判断へ戻すべきか、承認待ちとして扱うべきか、委任範囲外として扱うべきか、責任主体未確定として扱うべきかを判断する。

ただし、DAAGDは外部に存在しない権限を新しく生成するものではない。  
DAAGDは、既に存在する方針、権限、委任、承認条件、責任分界の範囲内で、MARGD内の authority / accountability state を判断する。

SDAGD は、SPPGDの判断構造と、DAAGDが判断した authority / accountability state を監査する。  
SDAGDは、戦略判断そのものを作らず、DAAGDを代替せず、正式な承認、実行許可、最終意思決定、責任主体の確定を行わない。

SDAGDが示すのは、あくまで監査上の状態である。  
たとえば、監査上の重大な阻止条件なし、条件付き監査所見あり、修復戻し、監査上の無効化などの状態を示す。

---

## 7. conditional watchdog

conditional watchdog domain extensions は、特定条件で監査状態を確認するためのGDである。

本prototypeでは、SDMRGD がこれに当たる。

```text id="gjau2c"
SDMRGD:
  SDAGDの監査状態をメタレビューする
```

SDMRGD は、SDAGDの監査範囲、監査根拠、監査結果分類、過剰監査、過少監査、形式的通過の危険、修復の必要性、DAAGD領域への越境などを見る。

ただし、SDMRGDはSDAGDのprimary auditを代行しない。  
また、戦略判断そのものを直接監査するGDでもなく、DAAGDの authority / accountability 判断を代替するGDでもない。

SDMRGDにおけるエスカレーションは、外部の最終判断や承認へ直接進めることではない。  
基本的には、SDAGD側の自己監査、修復、再監査、または上位runtime側の条件確認へ戻すことである。

---

## 8. ordinary domain extensions

ordinary domain extensions は、各専門領域の観点から、専門的意見、判断材料、確認条件、検出結果、危険の指摘、修復候補、引き渡し材料を出すGD群である。

```text id="62mwei"
ordinary domain extensions:
  専門的意見を出す
  判断材料を出す
  検出結果を出す
  確認条件を出す
  危険の指摘を出す
  修復候補を出す
  引き渡し材料を出す
```

ordinary domain extensions は、実行許可を出すものではない。  
また、最終決定、承認、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態を判断するものでもない。

たとえば、SEGDはsoftware engineeringの観点から検証状態や修復条件を出す。  
AISGDはAI securityの観点から危険条件や確認条件を出す。  
OMRGDは運用・信頼性の観点から状態や回復条件を出す。

ordinary domain extensions の出力は、SPPGDにおける戦略判断構造の材料、またはDAAGDにおける authority / accountability 判断の入力や参照材料にはなりうる。

しかし、それ自体は戦略判断構造そのものでも、MARGD内の authority / accountability 判断そのものでもない。

MARGD内で、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態として扱われるものは、DAAGDの authority / accountability 判断である。

---

## 9. templates

本prototypeには、bundle template と domain GD common skeleton template がある。

bundle template は、bundle構造を作るためのtemplateである。  
domain GD common skeleton template は、domain GDを作るための共通骨格である。

これらは、実際の専門判断を行うGDではない。

```text id="j2j0p0"
templates:
  構造を作るためのもの

templates are not:
  専門判断を行うGD
  CDOGDの代替
  ARGD / DAGDの代替
  domain extensionそのもの
  authority / accountability 判断を行うGD
  監査を行うGD
```

domain GD common skeleton template は、将来的に別分野のGDを作るときにも使えるよう、特定分野に閉じない形で作られている。

templateは、構造上の雛形であり、特定runtimeにおける権限、承認、実行許可、責任主体を自動的に与えるものではない。

---

## 10. architecture上の重要な分離

本prototypeのarchitectureで重要なのは、次の分離である。

```text id="wf9ltp"
reasoning:
  ARGD

behavior governance:
  DAGD

cross-domain orchestration:
  CDOGD

専門的判断材料:
  ordinary domain extensions

戦略判断構造:
  SPPGD

authority / accountability 判断:
  DAAGD

戦略判断構造と authority / accountability state の監査:
  SDAGD

SDAGD監査状態のメタレビュー:
  SDMRGD

component container:
  bundle
```

この分離により、専門的な判断材料、戦略判断構造、authority / accountability 判断、監査、メタレビュー、routingが混ざりにくくなる。

ordinary domain extensions は、専門的意見、判断材料、確認条件、危険の指摘、修復候補、引き渡し材料を出す。  
それらの出力は、SPPGDやDAAGDへの入力や参照材料にはなりうるが、それ自体は戦略判断構造そのものでも、MARGD内の authority / accountability 判断そのものでもない。

SPPGDは、戦略判断の構造を整理する。  
DAAGDは、MARGD内で authority / accountability 判断を担当する。  
SDAGDは、SPPGDの判断構造とDAAGDが判断した authority / accountability state を監査する。  
SDMRGDは、SDAGDの監査状態をメタレビューする。  
CDOGDは、これらのdomain間のrouting、scope調整、handoff、repair propagation を扱う。

---

## 11. 権限に関する注意

MARGDおよび各GDは、上位権限、system policy、developer policy、runtime policy、tool権限、外部実行権限、人間の承認権限、責任主体を変更するものではない。

また、AIに新しい実行権限を与えるものでもない。

```text id="architecture_authority_limits"
MARGDが変更しないもの:
  system policy
  developer policy
  runtime policy
  tool権限
  外部実行権限
  人間承認条件
  組織上の責任主体
  法令・制度上の責任
```

このprototypeは、与えられたruntimeまたは対話層の内部で、どのgovernance scopeを参照し、  
どの範囲で適用すべきかを動的に整理しやすくするためのgovernance layerである。

MARGDを通常のLLM対話上で使う場合、主に判断材料、構造、監査、権限境界、人間判断への引き渡し条件を整理する。

MARGDをAgentic AIやtool runtimeに組み込む場合でも、実際の実行可否、tool利用可否、外部操作可否、承認条件、責任主体は、runtime policy、tool権限、外部権限、人間、組織、制度によって決まる。

詳細は、`usage_and_limitations_ja.md` を参照すること。