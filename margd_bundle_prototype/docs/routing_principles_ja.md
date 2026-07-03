# Routing Principles

この文書では、MARGD Runtime Governance Bundle Prototype におけるroutingの考え方を説明する。

ここでいうroutingとは、どのGDを、どの範囲で、どの役割として働かせるかを整理するための考え方である。  
これは、実行許可、承認、責任主体の確定、最終決定を意味しない。

---

## 1. routingの基本

本prototypeでは、GDがbundleに入っているだけでは、そのGDが常に働くわけではない。

```text id="3r9jaf"
loaded != active
registered != active
reference != governance
registration != activation
```

GDがbundleに登録されていることと、そのGDが現在のtaskで有効になることは別である。  
また、GDが参照可能であることと、そのGDが判断権限を持つことも別である。

routingの目的は、現在のtaskに対して、どのGDがどの範囲で必要か、どの役割で関係するか、どこで引き渡すべきかを整理することである。

---

## 2. CDOGDの役割

CDOGD は、複数のGDを横断してまとめるための orchestration GD である。

CDOGDは、domain名や固定順序だけでGDを選ぶものではない。  
また、固定された優先順位表や固定された所有domain表によって処理を決めるものでもない。

```text id="5dba3a"
CDOGDが見るもの:
  taskの内容
  対象
  必要なgovernance
  registered manifest
  capability
  role
  非対象条件
  根拠
  runtime context
```

CDOGDは、これらをもとに、どのGDをどの範囲で扱うか、どのroleで関係させるか、どこで抑制・弱化・引き渡し・修復伝播するかを整理する。

ただし、CDOGDは最終決定を行わない。  
CDOGDは、承認、実行許可、責任主体の割当、authority / accountability 判断、専門判断そのものを代替しない。

---

## 3. routingは権限付与ではない

routingによって、あるGDが現在のtaskに関係すると整理されても、それは権限付与を意味しない。

```text id="52zprf"
routing does not mean:
  実行許可
  最終決定
  承認
  責任主体の割当
  tool権限の追加
  外部実行権限の追加
```

GDの起動や参照は、あくまでgovernance scopeの選択である。  
どの観点を参照するか、どの範囲で確認するか、どのGDへ引き渡すかを整理するためのものである。

利用上の権限境界については、`usage_and_limitations_ja.md` を参照すること。

---

## 4. 固定順序ではない

本prototypeでは、GDの分類や記載順は、優先度や起動順を意味しない。

```text id="0k32nk"
bucket order != priority
file order != priority
registry order != priority
domain name != routing result
```

たとえば、`ordinary/` に置かれているGDが、必ず後回しになるわけではない。  
また、`decision_pipelines/` に置かれているGDが、常に先に働くわけでもない。

routingは、現在のtask、対象、根拠、必要なgovernance、runtime contextに応じて決まる。

---

## 5. domain名だけでは決めない

CDOGDは、domain名やkeywordだけでroutingしない。

たとえば、task内に「security」という語があるだけで、必ずAISGDが主役になるわけではない。  
「architecture」という語があるだけで、必ずAIAGDが主役になるわけでもない。

重要なのは、そのtaskで何を扱おうとしているかである。

```text id="g3ijlu"
見るべきもの:
  何が対象か
  何を判断するのか
  何を出力するのか
  どの専門観点が必要か
  どの判断材料が必要か
  authority / accountability 判断が必要か
  監査が必要か
  人間判断に戻す必要があるか
```

domain名は手がかりにはなるが、それだけでroutingを決めるものではない。

---

## 6. routingが成立する理由と設計上のこだわり

このroutingが成立する前提の1つは、domain名、component id、file名、bucket名、登録順、固定owner、固定priorityのような固有名詞や固定値に、routing logicをできるだけ依存させないことである。

可能な限りハードコードを避け、抽象化を行っている。

GDが増える、名前が変わる、似た領域のGDが追加される、runtime contextが変わる、roleが変わるたびに固有名詞分岐を追加していくと、routing logicはすぐに保守不能になる。

そのため、このprototypeでは、ハードコードが避けられない識別・参照・記録・version管理は残しつつ、抽象化できる箇所はできるだけ抽象化している。

routingで見るべきものは、名前そのものではなく、そのGDが何を扱えるか、何を扱わないか、現在のtaskに必要か、どの範囲で関係するか、どのroleで働くか、どこで抑制・弱化・引き渡しが必要か、どの根拠があるかである。

つまり、IDなどは名札であり、routing判断そのものではない。  
MARGDでは、名札ではなく、職務定義、適用範囲、非対象条件、runtime context、根拠を見る。

---

## 7. function role

GDが起動する場合でも、そのGDが常に主役になるわけではない。

同じGDでも、taskによって役割が変わる。

```text id="5ajhpd"
role examples:
  primary
  supporting
  validation
  reference
  suppressed
```

たとえば、SEGDが主役になる場合もあれば、AIAGDの判断材料を確認する補助役になる場合もある。  
AISGDが主役になる場合もあれば、AI security risk が軽く関係するだけの補助役になる場合もある。

function role は、taskごとに決まる。  
GDの登録位置やファイル順だけで決まるものではない。

---

## 8. ordinary domain extensions のrouting

ordinary domain extensions は、各専門領域の観点から、専門的意見、判断材料、検出結果、確認条件、危険の指摘、修復候補、引き渡し材料を出すGD群である。

```text id="1hqgfq"
ordinary domain extensions:
  専門的意見を出す
  判断材料を出す
  検出結果を出す
  確認条件を出す
  危険の指摘を出す
  修復候補を出す
  引き渡し材料を出す
```

ordinary domain extensions は、実行許可を出さない。  
また、最終決定、承認、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態を判断しない。

たとえば、DSGDはdata scienceの観点から分析妥当性を確認する。  
SEGDはsoftware engineeringの観点から検証状態や修復条件を確認する。  
OMRGDは運用・信頼性の観点から状態や回復条件を確認する。

ordinary domain extensions の出力は、SPPGDにおける戦略判断構造の材料、  
またはDAAGDにおける authority / accountability 判断の入力や参照材料にはなりうる。

しかし、それ自体は戦略判断構造そのものでも、MARGD内の authority / accountability 判断そのものでもない。

MARGD内で、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態として扱われるものは、DAAGDの authority / accountability 判断である。

---

## 9. DAAGDの位置

DAAGD は、MARGD内で authority / accountability 判断を担当するGDである。

DAAGDは、既存のsystem policy、developer policy、runtime policy、tool権限、外部実行権限、委任条件、承認条件、責任分界に基づき、  
当該出力・判断候補・実行候補をAIまたはruntimeの自律判断として扱えるか、人間判断へ戻すべきか、承認待ちとして扱うべきか、委任範囲外として扱うべきか、責任主体未確定として扱うべきかを判断する。

```text id="mg21co"
DAAGDが見るもの:
  AI判断は助言に留まるのか
  判断支援なのか
  provisional recommendationなのか
  条件付き判断なのか
  委任された判断なのか
  autonomous execution decisionなのか
  人間判断へ戻すべきか
  承認待ちとして扱うべきか
  委任範囲内か委任範囲外か
  責任主体は成立しているか未確定か
  記録条件は満たされているか
```

ただし、DAAGDは外部に存在しない権限を新しく生成するものではない。  
DAAGDは、既に存在する方針、権限、委任、承認条件、責任分界の範囲内で、MARGD内の authority / accountability state を判断する。

---

## 10. decision pipeline への引き渡し

routingでは、ordinary domain extensions から decision pipeline へ判断材料が渡されることがある。

典型的には、次のような流れになる。

```text id="d8kntj"
ordinary domain extensions:
  専門的な判断材料、確認条件、危険の指摘、修復候補、引き渡し材料を出す

SPPGD:
  ordinary系GDなどから渡された材料を、戦略判断構造の材料として扱う
  目的、前提、制約、選択肢、優先順位、継続、停止、撤退、再評価条件などを整理する

DAAGD:
  MARGD内で authority / accountability 判断を担当する
  自律判断として扱えるか、人間判断へ戻すべきか、承認待ちか、委任範囲外か、責任主体未確定かを判断する

SDAGD:
  SPPGDの判断構造と、DAAGDが判断した authority / accountability state を監査する

SDMRGD:
  SDAGDの監査状態をメタレビューする
```

この流れは固定pipelineではない。  
taskによって、一部のGDだけが関係する場合もある。

重要なのは、専門判断材料、戦略判断構造、authority / accountability 判断、監査、メタ監査を混ぜないことである。

---

## 11. activationの範囲

GDが起動する場合でも、そのGDの全機能が常に働くわけではない。

```text id="kz4z02"
activation is scope-limited:
  現在のtaskに必要な範囲だけ働く
  必要なfunction roleだけ持つ
  不要な部分は働かない
  関係が薄いGDはreferenceに留まる
  関係しないGDは起動しない
```

たとえば、AISGDが関係しても、すべてのAI security観点を網羅する必要があるとは限らない。  
SEGDが関係しても、software engineering全体を扱うとは限らない。

GDの起動は、task-localである。

---

## 12. 再評価

routingは一度決めたら終わりではない。

taskの前提、対象、制約、risk、出力要求、authority / accountability state が変われば、関係するGDも変わる。

```text id="0wbp8f"
再評価が必要になる例:
  対象が変わった
  前提が変わった
  制約が変わった
  riskが変わった
  出力形式が変わった
  人間承認が必要になった
  実行判断が関係してきた
  監査が必要になった
```

このため、domain activation は一度きりの固定状態ではない。  
taskやcontextの変化に応じて、必要な範囲で再評価され、必要に応じて再び呼び出される。

---

## 13. まとめ

本prototypeのroutingは、固定順序やdomain名で決まるものではない。  
CDOGDが、task、対象、必要なgovernance、registered manifest、capability、role、根拠、runtime contextをもとに、どのGDをどの範囲で扱うか、どのroleで関係させるかを整理する。

ただし、routingは権限付与ではない。  
GDが起動しても、AIの実行権限、tool権限、外部操作権限、人間承認、責任主体が変更されるわけではない。

ordinary domain extensions は、専門的意見、判断材料、確認条件、危険の指摘、修復候補、引き渡し材料を出す。

ordinary domain extensions の出力は、SPPGDにおける戦略判断構造の材料、  
またはDAAGDにおける authority / accountability 判断の入力や参照材料にはなりうる。  
しかし、それ自体は戦略判断構造そのものでも、MARGD内の authority / accountability 判断そのものでもない。

MARGD内で、自律判断可否、承認待ち状態、委任範囲内外、責任主体成立状態として扱われるものは、DAAGDの authority / accountability 判断である。

詳細な利用上の注意と限界は、`usage_and_limitations_ja.md` を参照すること。