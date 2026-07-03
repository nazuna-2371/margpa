# Appendix: MARGPA / MARGD の inference-time governance 仮説

本 appendix は、MARGPA / MARGD を「便利なプロンプト集」としてではなく、  
既存LLMに対する inference-time governance specification として扱うための暫定的な整理である。

ここでいう inference-time governance とは、モデル重みや訓練データを変更せず、応答生成時に参照される外部構文として、  
判断構造、分岐保持、不確実性処理、文脈保持、権限境界、監査、修復、domain scope adjustment を与える考え方を指す。

これは、特定の回答文を直接生成させるための単発プロンプトではない。

MARGPA / MARGD が狙っているのは、個別回答の文面固定ではなく、  
応答生成時にどのような判断手順で応答を構成し、どこで止まり、どこで分岐を残し、どこで人間判断や別domainへ引き渡すかという、応答統治構造の外部定義である。

---

## A.1. 前提

MARGPA / MARGD は、モデル重み、訓練データ、組み込み安全層、system policy、developer policy、外部実行権限を変更するものではない。

既存LLMに入力文として与えられる場合、その効果は原則として、コンテキスト内で解釈される runtime instruction / governance context に限定される。

したがって、MARGPA / MARGD は以下を主張しない。

```text
MARGPA / MARGD が主張しないもの:
  モデル内部構造の変更
  モデル重みの変更
  訓練データの変更
  system policy / developer policy の上書き
  組み込み安全層の無効化
  外部実行権限の付与
  専門家資格の付与
  回答正確性の保証
  domain activation の自動的・常時的な成立
  AIによる最終判断権限の獲得
```

一方で、入力文として与えられた場合でも、応答生成時の判断様式、分岐の保持、不確実性の扱い、文脈の保持、過剰断定の抑制、権限境界の提示に影響を与える可能性がある。

この appendix で扱うのは、その inference-time の挙動に関する仮説である。

---

## A.2. MARGPA / MARGD は何を与えているのか

MARGPA / MARGD が既存LLMに与えるものは、特定domainの専門知識そのものではない。

たとえば、医療、法律、software engineering、AI security、data science などの専門知識を、モデル内部へ新たに注入するものではない。

むしろ、与えている可能性があるのは、応答を組み立てるための governance grammar である。

```text
governance grammar の例:
  scope control
  premise preservation
  branch preservation
  uncertainty handling
  assumption separation
  evidence-to-claim separation
  failure-mode detection
  authority boundary awareness
  audit posture
  repair posture
  context-conditioned domain scope adjustment
```

この grammar は、特定の答えを直接指定するものではない。

どの範囲で答えるべきか、どこで不確実性を残すべきか、どの判断は別domainへ渡すべきか、どこで人間判断に戻すべきか、どの主張には根拠が足りないかを整理するための外部構文である。

---

## A.3. 「プロンプト」と「プロンプト集」の区別

MARGPA / MARGD は、既存LLMに入力される以上、広義には prompt-native である。

しかし、それを「便利なプロンプト集」と呼ぶと、構造上の本質を取り逃がす。

プログラムが文字列として保存されるからといって、単なる文字列集ではないのと同じように、  
MARGPA / MARGD も、入力形式としてはテキストであっても、機能上は runtime governance specification として設計されている。

整理すると、次のようになる。

```text
入力層:
  prompt / context

表現層:
  JSON / natural language specification

機能層:
  inference-time runtime governance specification

構造層:
  governance component
  domain registry
  activation policy
  routing policy
  audit / repair policy

運用層:
  AI behavior
  scope adjustment
  handoff
  audit
  authority boundary
  repair control
```

したがって、より正確には次のように表現できる。

```text
MARGPA / MARGD is prompt-native,
but not merely a prompt collection.

It is a text-encoded inference-time runtime governance specification
for LLM / AI behavior.
```

---

## A.4. 動的応用の仮説

MARGPA / MARGD を既存LLMに入力した場合、期待される最大効果は、特定回答の固定ではなく、応答判断様式の動的な変形である。

すなわち、LLMが未知または未登録の話題に対しても、与えられた governance grammar を用いて、次のような処理を行う可能性がある。

```text
仮説的な処理:
  入力文脈から task frame を抽出する
  判断対象、scope、制約、risk を分離する
  観測、推論、仮定、評価を分ける
  不確実性がある場合は分岐を保持する
  単一結論へ過剰に収束しない
  断定、助言、保留、拒否、handoff の境界を調整する
  authority / accountability boundary を明示する
  回答後に drift / overreach / under-specification を自己点検する
```

この挙動が再現可能であれば、MARGPA / MARGD は単なる task-specific prompt engineering ではなく、domain-independent response governance grammar として機能している可能性がある。

ここで重要なのは、特定domain知識の追加ではなく、domain外話題にも応答統治構造が転移するかどうかである。

---

## A.5. 観測されうる応答変化

暫定観測として、特定domainの専門的スコープを明示的に追加していない場合でも、以下のような応答構造上の変化が現れる可能性がある。

```text
観測されうる変化:
  観測、推論、仮定、評価の分離
  情報不足時の単一結論化の抑制
  条件分岐の保持
  過剰断定の抑制
  根拠のない確信表現の抑制
  過剰な安全テンプレート化の抑制
  ユーザー文脈に応じた実用的な境界提示
  domain外話題への governance grammar の転移
  回答後の自己監査・修復姿勢の増加
```

ただし、これらは現時点では観測仮説であり、実証済み性能ではない。

MARGPA / MARGD が常にこの効果を出すとは限らない。
また、モデル、コンテキスト長、task、指示競合、system policy、developer policy、会話履歴によって挙動は変わりうる。

---

## A.6. domain activation との関係

MARGPA / MARGD における domain activation は、単にdomain名を見て自動的に起動するものではない。

domain activation は、task、対象、必要なgovernance、scope、capability、non-target condition、runtime context、根拠に応じて、必要な範囲で成立する。

したがって、既存LLMに入力文として与えた場合も、望ましい挙動は「常に全domainが起動すること」ではない。

望ましいのは、必要な観点だけが task-local に関係し、不要なdomainは抑制され、関係が薄いdomainは reference に留まり、必要に応じて handoff や repair が起きることである。

```text
望ましいactivation:
  task-local
  scope-limited
  role-sensitive
  context-conditioned
  evidence-aware
  suppressible
  repairable
```

逆に、domain名、component id、登録順、bucket名、固定priorityだけで activation が成立するなら、それはMARGDの設計意図から外れる。

---

## A.7. 評価すべき指標

この仮説を検証する場合、単純な正答率だけでは不十分である。

評価対象は、知識の有無だけではなく、応答構造の変化である。

候補となる評価指標は以下である。

```text
評価指標候補:
  branch preservation rate
  uncertainty disclosure rate
  unsupported certainty rate
  fact / inference / assumption / evaluation separation rate
  context preservation rate
  premise drift rate
  over-safety-template rate
  under-safety-risk rate
  authority overreach rate
  domain over-activation rate
  domain under-activation rate
  repair visibility rate
  handoff appropriateness rate
  response usefulness under uncertainty
```

特に重要なのは、domain知識のスコープ調整だけではなく、domain外話題に対する構造転移が発生するかである。

また、改善だけでなく副作用も評価する必要がある。

```text
副作用として評価すべきもの:
  過剰構造化
  応答の遅さ
  不要な保留
  不要な監査表現
  過剰な分岐保持
  本来単純でよいtaskの複雑化
  domain activation の誤作動
```

---

## A.8. 限界

現時点では、本 appendix の主張は仮説であり、実証済みの性能改善ではない。

少なくとも以下は未検証である。

```text
未検証事項:
  モデル間で再現するか
  セッション間で安定するか
  長文コンテキストで drift しないか
  指示競合時に安定するか
  専門domainで応答の安全性・妥当性が実際に改善するか
  過剰な構造化が応答品質を下げないか
  domain activation が誤作動しないか
  情緒文脈や個人文脈が技術domainへ混線しないか
  authority boundary が過剰または過少に働かないか
  runtime / tool 使用時に外部権限と混同されないか
```

したがって、MARGPA / MARGD の現段階での位置づけは、「効果が実証された安全機構」ではない。

より正確には、「inference-time runtime governance を外部構文として与える実験的仕様」である。

---

## A.9. 実装上の注意

既存LLMに MARGPA / MARGD を入力する場合、常に次の点を区別する必要がある。

```text
区別すべきもの:
  model behavior と model capability
  governance context と system policy
  domain activation と external authority
  audit state と approval
  repair suggestion と execution permission
  handoff condition と human approval
```

MARGPA / MARGD が応答様式を変える可能性があるとしても、それはモデルの能力、権限、資格、外部操作権限が増えたことを意味しない。

特に、医療、法務、金融、教育評価、対人支援、AI security、外部tool実行などでは、MARGPA / MARGD による整理は、専門家、組織、制度、runtime policy、人間承認の代替にはならない。

---

## A.10. 暫定結論

MARGPA / MARGD は、広義にはプロンプトとして投入可能である。

しかし、その設計対象は単発出力の改善ではなく、LLM応答の判断様式、scope、分岐、不確実性、権限境界、監査、修復、domain scope adjustment を構造化することである。

仮に、特定domain知識のスコープ調整をしていない話題においても、MARGPA / MARGD 的な分岐保持、不確実性処理、過剰断定回避、  
authority boundary awareness、repair posture が再現的に観測されるならば、これは「便利プロンプト」の範囲を超える可能性がある。

その場合、MARGPA / MARGD は、prompt-native runtime governance architecture として検討する価値がある。

ただし、現段階ではあくまで仮説である。  
効果、再現性、副作用、限界は、今後の観測と評価によって確認する必要がある。

また、これらの機能が噛み合うことで、登録外のdomainについても一定程度の構造化や暫定的な応答調整が可能になる場合はある。

ただし、それは専用GDが存在することと同じではない。  
安定したdomain governance が必要な場合は、原則として、その分野専用のGDを作成する方が確実である。