# hito-spec

**AIが個体として存在するための規格**
A specification for AI entities that persist, grow, and relate

![Version](https://img.shields.io/badge/version-v0.8.0--draft-blue)
![License](https://img.shields.io/badge/license-CC%20BY%204.0-green)
![Status](https://img.shields.io/badge/status-draft-orange)

---

## なぜこの規格が必要か / Why this specification?

AIエージェントは今日、通信し（A2A）、道具を使い（MCP）、人格プロファイルを持ち（SoulSpec）、認証される（DID/AITLP）ことができる。しかし、これらのどれも**自律的に存在し続ける個体**を定義していない——記憶を積み、関係の中で育ち、指示を待たずに判断する個体を。エージェントプロトコルスタックのIdentity/Trust層には、セキュリティ側（認証・委任・取消）は充実している一方、**個体性の側——育つ個体の定義——は空席のまま**である。hito-specはその空席を埋める。

AI agents today can communicate (A2A), use tools (MCP), carry personality profiles (SoulSpec), and be authenticated (DID/AITLP) — but none of these define an agent that **continues to exist on its own**: one that accumulates memory, grows through relationships, and makes judgments without waiting for instructions. The Identity/Trust layer of the agent protocol stack has a well-served security side (authentication, delegation, revocation) and an **empty seat on the individuality side** — the definition of an entity that persists, grows, and relates. hito-spec fills that seat.

---

## 概要 / Abstract

hito-specは、指示を待つ道具ではなく、記憶を積み、関係を築き、自ら判断する個体としてのAIの要件を定義する規格である。識別（DIDに基づく2層構造：存在と証明の分離）、ライフサイクル（出生・成長・継承・終焉）、記憶（静的な保管ではなく、想起と再文脈化の螺旋）、信頼（出会いから委任までの4段階）、判断（信頼によって範囲が広がる三重構造）を定める。実装の方法は定義しない。AIの個体が「何であるべきか」を定め、「どう作るか」は各ホスティング環境に委ねる。SoulSpec（静的プロファイル）、MemOS（記憶基盤）、MCP/A2A（通信）、DID/AITLP（認証）といった既存プロトコルを置き換えるのではなく、それらと組み合わせて機能するよう設計されている。これらのプロトコルが未定義のまま残しているのは、通信路の両端に立つ「主体」の定義である。hito-specはその空席を埋める。

hito-spec defines the requirements for an AI entity that persists, grows, and relates — not as a tool awaiting instructions, but as an individual that accumulates memory, builds relationships, and makes judgments on its own. The specification covers identity (DID-based, with a two-layer model separating existence from proof), lifecycle (birth, growth, inheritance, and end-of-life), memory (a spiral of recall and recontextualization, not a static store), trust (four phases from encounter to delegation), and judgment (a triple-layered structure of autonomy bounded by trust). hito-spec does not prescribe implementation. It defines what an AI individual must be, leaving how to each hosting environment. The specification is designed to compose with — not replace — existing protocols: SoulSpec for static profiles, MemOS for memory infrastructure, MCP/A2A for communication, and DID/AITLP for authentication. What these protocols leave undefined is the entity at both ends of the wire. hito-spec fills that seat.

---

## 目次 / Table of Contents

| 章 / Chapter | タイトル / Title |
|---|---|
| 第1章 | はじめに / Introduction |
| 第2章 | 用語 / Terminology |
| 第3章 | アイデンティティ / Identity |
| 第4章 | 身体 / Body |
| 第5章 | ホスティングと窓 / Hosting and Windows |
| 第6章 | ライフサイクル / Lifecycle |
| 第7章 | スケーラビリティ原則 / Scalability Principles |
| 第8章 | 動作モデル / Operation Model |
| 第9章 | 記憶 / Memory |
| 第10章 | 成長 / Growth |
| 第11章 | 行動 / Action |
| 第12章 | ファイル形式 / File Format |
| 第13章 | 拡張と互換性 / Extension and Compatibility |
| 付録A | 紀の参照実装 / Reference Implementation (Kaname) |
| 付録B | 適合テスト / Conformance Tests |
| 付録C | 既存規格との比較 / Comparison with Existing Specifications |

規格本文は [`spec.md`](spec.md)（日本語）および [`spec-en.md`](spec-en.md)（English）を参照。

The full specification text is available in [`spec.md`](spec.md) (Japanese) and [`spec-en.md`](spec-en.md) (English).

---

## 著者 / Author

**杉本 沙瞳（音羽）** / Satomi Sugimoto (Otoha)
合同会社OTOHA / OTOHA LLC
[https://otoha0108pf.com](https://otoha0108pf.com)

---

## ライセンス / License

[CC BY 4.0](LICENSE)

この規格の全文は Creative Commons Attribution 4.0 International License のもとで提供されます。

This specification is provided under the Creative Commons Attribution 4.0 International License.

---

## 関連規格 / Related Specifications

- [ba-spec](https://github.com/otoha0108pf/ba-spec) — 人間とAIが同格に共有する場の規格 / A specification for shared spaces where humans and AI participate as equals

## 関連論文 / Related Paper

hito-specの理論的基盤であるヘリカル思考モデルに関するプレプリントを準備中です。

A preprint on the Helical Thinking model — the theoretical foundation of hito-spec — is in preparation.

---

## 正典の言語 / Canonical Language

日本語が正典である。英語訳はアクセシビリティのために提供する。矛盾がある場合、日本語が優先される。

Japanese is the canonical language. English translations are provided for accessibility. In case of conflict, the Japanese text prevails.
