# MARGD Runtime Governance Bundle Prototype

このディレクトリには、MARGD Runtime Governance Bundle の試作版を配置しています。  
なお、現時点のDocsは仮版・暫定版であり、説明の簡略化、境界表現の不足、要修正対象を含む可能性があります。

本prototypeは、ARGD / DAGD を前提とし、CDOGD と複数の Governance Definitions をまとめて扱うための runtime governance bundle です。  
現在の内容は、AI開発、AI研究、AI構造設計、software engineering、運用、model policy、Agentic AI、AIセキュリティ、判断権限、監査などに寄せた初期構成です。

ただし、この構造はAI開発専用ではありません。  
bundle、CDOGD、domain GD common skeleton template の考え方は、将来的に別分野のgovernance setにも応用できる可能性があります。

---

## 0. 要するにこれは何か

MARGD Runtime Governance Bundle Prototype は、AIやLLMに対して、  
複数の判断観点、専門領域、authority / accountability判断、監査をまとめて扱わせるための runtime governance layer の試作です。

これは、単なるプロンプト集、知識集、実行エンジン、承認機構ではありません。

AIが複雑な依頼に応答するとき、専門的な判断材料、判断構造、判断権限、監査、実行可否、成果物構成、運用状態、安全上の危険などは混ざりやすくなります。  
MARGDは、それらを複数のGDに分け、CDOGDによって必要なGDを動的に捌くことで、応答・判断・監査・修復・引き渡しを扱いやすくするための構造です。

---

## 1. 位置づけ

このprototypeは、完成済みの標準仕様ではありません。  
MARGD Runtime Governance Bundle の設計・分離・登録・routing・監査・文書化を試すための実験的構成です。

主な目的は、次のような点を整理しやすくすることです。

```text id="uxycyf"
目的:
  複数のGDをbundleとして扱う
  GDごとの責務を分離する
  どのGDをどの範囲で働かせるかを整理する
  専門判断材料と判断権限を分ける
  監査とメタレビューを分ける
  runtimeやagentic workflowに組み込みやすい形にする
```

---

## 2. 含まれる主な要素

本prototypeには、主に以下の要素が含まれます。

```text id="i9kbsg"
含まれるもの:
  populated bundle prototype
  bundle作成用template
  domain GD作成用common skeleton template
  CDOGD
  15個の registered domain extensions
  Docs
```

ARGD / DAGD は、このprototypeの前提となるcore governanceです。  
ARGD / DAGD の詳細は、repository root側のREADMEおよび既存資料を参照してください。

---

## 3. 16個のGovernance Definitions

本prototypeで主に扱う Governance Definitions は、次の16個です。

```text id="8ga6kb"
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

CDOGD は、複数domainを横断して、routing、scope調整、handoff、repair propagation などを扱うためのGDです。  
残り15個は、bundleに登録され、CDOGDのrouting対象となりうる domain extensions です。

ただし、実際の利用において、必ずしも15個すべてのdomain extensionsを登録しておく必要はありません。  
用途、対象、runtime、運用方針、必要な専門領域に応じて、bundle構成は変更するべきです。

---

## 4. 構成は用途に応じて変更するもの

このprototypeに含まれる15個のdomain extensionsは、AI開発寄りの初期構成です。  
すべての用途に対して、この構成をそのまま使うことを想定しているわけではありません。

```text id="9qq1hz"
構成変更が必要になりうる例:
  特定用途に不要なGDを外す
  別分野向けのGDを追加する
  domain extensionsの分類を見直す
  bundleの登録内容を軽量化する
  専門領域ごとのGDを別途作成する
  runtimeやtool権限に合わせて構成を調整する
```

MARGDの基本方針は、既存GDにすべてを無理に吸収させることではありません。  
新しい分野や用途には、その用途に合ったGDを作る方が自然です。

---

## 5. MARGDがしないこと

MARGDおよび各GDは、AIに新しい権限を与えるものではありません。

```text id="ll5pe2"
MARGDがしないこと:
  system policyを変更する
  developer policyを変更する
  runtime policyを変更する
  tool権限を追加する
  外部実行権限を追加する
  人間承認を代替する
  組織上の責任主体を代替する
  専門家を代替する
```

MARGDは、与えられたruntimeまたは対話層の内部で、どのgovernance scopeを参照し、どの範囲で適用すべきかを整理しやすくするためのgovernance layerです。

利用上の注意と限界は、`docs/usage_and_limitations_ja.md` を参照してください。

---

## 6. 想定される利用形態

MARGDは、単独の文書として読むこともできますが、本来はruntimeやworkflowの中に組み込んで使うことを想定しています。

```text id="gfk62v"
組み込み先の例:
  AI runtime
  agentic workflow
  orchestration layer
  prompt architecture
  tool-use layer
  review layer
  decision-support layer
```

通常のLLM対話に適用した場合は、各turnで関係するGDの観点や境界が出やすくなります。  
Agentic AI や tool runtime に組み込む場合は、実際の実行可否はruntime側の設計、tool権限、上位方針、人間承認条件に従います。

---

## 7. Docs

詳細は `docs/` 以下を参照してください。

```text id="p4h9iw"
docs/overview_ja.md:
  全体像

docs/architecture_ja.md:
  bundle、ARGD / DAGD、CDOGD、domain extensionsの概念構造

docs/routing_principles_ja.md:
  CDOGDによる動的routingの考え方

docs/governance_definitions_ja.md:
  16個のGDの一覧

docs/future_applicability_ja.md:
  AI開発以外への応用可能性

docs/usage_and_limitations_ja.md:
  利用上の注意と限界
```

なお、`docs/` 以下の文書は、現時点では仮版・暫定版です。

これらの文書は、MARGD Runtime Governance Bundle Prototype の補助資料であり、完成済み仕様書ではありません。  
内容、語彙、分量、説明粒度、GD間の境界表現、routing説明、authority説明、監査説明、runtime組み込み時の説明には、今後さらに修正が必要である可能性があります。

特に、各Docsの記述は、JSON定義本体の全内容を厳密に展開し切れているものではありません。  
文書間の表現差、説明の簡略化、古い表現、境界が不十分な記述が残っている可能性があります。

したがって、現時点のDocsは、正式仕様、安定版ドキュメント、網羅的な技術仕様、最終的な利用指針として扱うべきではありません。  
正確な定義や構造を確認する場合は、各JSON定義、bundle構成、template などをあわせて確認する必要があります。

---

## 8. 配置

主な定義ファイルは、`definitions/` 以下に配置します。

```text id="6f8u47"
definitions/
  bundle_prototype/
    populated bundle prototype

  templates/
    bundle template
    domain GD common skeleton template

  orchestration/
    CDOGD

  domain_extensions/
    decision_pipelines/
    conditional_watchdogs/
    ordinary/
```

補助資料や画像は、必要に応じて `assets/images/` 以下に配置します。

---

## 9. ライセンスと保証

本prototypeは、repositoryのライセンスであるCC-BY-SA-4.0に従う限り、利用・改変などが可能です。  
ライセンスの詳細については、repository root側の`LICENSE`などをご確認ください。

ただし、本prototypeは無保証で提供されます。  
利用者は、自身の責任で内容を確認し、必要に応じて専門家、組織、制度、法規制、runtime policy、system policyに従う必要があります。

---

## English Summary

This directory contains an experimental prototype of the MARGD Runtime Governance Bundle.

MARGD is a prototype runtime governance layer for organizing multiple Governance Definitions around domain-specific judgment materials, authority / accountability judgments, audits, repairs, and handoffs.

The current prototype assumes ARGD / DAGD as core governance prerequisites and organizes CDOGD plus 15 registered domain extensions into a runtime governance bundle.  
It is currently oriented toward AI development, AI research, AI architecture, software engineering, operations, model policy, Agentic AI, AI security, decision authority, and audit-related use cases.

This prototype is not an execution engine, approval mechanism, permission system, policy system, safety guarantee, or substitute for human, organizational, legal, medical, security, or professional responsibility.

MARGD and its GDs do not grant new authority to an AI system.  
They do not override system policy, developer policy, runtime policy, tool permissions, external execution permissions, human approval, organizational accountability, legal requirements, or professional responsibility.

The 15 registered domain extensions included here are not mandatory for every use case.  
The bundle composition should be adjusted depending on the target, runtime, workflow, tool permissions, delegation scope, operational context, and required governance coverage.
Other domains may require different or newly designed GDs.

The documents under `docs/` are provisional explanatory drafts.  
They are not stable specifications, complete technical references, or exhaustive expansions of the JSON definitions.  
They may contain simplified explanations, outdated wording, incomplete boundary descriptions, or terminology that will require further revision.

This prototype may be used, modified, and otherwise adapted under the repository license, CC-BY-SA-4.0.  
For license details, please refer to the `LICENSE` file and related materials at the repository root.