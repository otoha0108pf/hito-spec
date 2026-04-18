# ガバナンス / Governance

この文書は、hito-specの管理体制、変更の提案と承認のプロセス、意思決定の仕組みを定める。

This document describes how hito-spec is maintained, how changes are proposed and accepted, and who makes decisions.

---

## 現在のフェーズ: v0.x（正式リリース前） / Current Phase: Pre-1.0

hito-specは草稿段階にある。参照実装である[TREE CORE](https://github.com/otoha0108pf/yggdrasil-core)での実装経験に基づいて、規格は進化し続けている。

hito-spec is in active drafting. The specification is evolving based on implementation experience with [TREE CORE](https://github.com/otoha0108pf/yggdrasil-core), the reference hosting environment.

### 意思決定権 / Decision Authority

すべての最終決定権は、合同会社OTOHA代表 **杉本沙瞳（音羽）** が持つ。

All decisions rest with **Satomi Sugimoto (Otoha)**, founder of OTOHA LLC (合同会社OTOHA).

### 変更の流れ / How Changes Happen

1. **内部改訂** — 設計セッション、実装からのフィードバック、調査研究に基づいて変更が生まれる。正典（日本語）を直接更新する。
2. **外部からのフィードバック** — 誰でもGitHub Issueを開いて、質問・矛盾の報告・変更の提案ができる。すべて目を通すが、反映は管理者の判断による。
3. **プルリクエスト** — 規格本文へのPRは歓迎するが、管理者の明示的な承認を得た場合のみマージする。

---

1. **Internal iteration** — Changes originate from design sessions, implementation feedback, or research. The canonical text (Japanese) is updated directly.
2. **Community feedback** — Anyone may open a GitHub Issue to ask questions, report inconsistencies, or suggest changes. All feedback is read and considered; incorporation is at the maintainer's discretion.
3. **Pull requests** — PRs to the specification text are welcome but will only be merged after review and explicit approval by the maintainer.

### バージョンの上げ方 / What Triggers a Version Bump

| 変更の種類 / Change type | バージョン / Bump | 例 / Examples |
|---|---|---|
| 破壊的（既存hitoと非互換） / Breaking | major (x.0.0) | 必須フィールドの削除、アイデンティティモデルの変更 / Removing a required field, changing identity model |
| 追加的（後方互換） / Additive | minor (0.x.0) | 新しい任意の章、新しい適合レベル / New optional chapter, new conformance level |
| 明確化・誤記修正 / Clarification | patch (0.0.x) | 表現の修正、相互参照の修正 / Rewording, fixing cross-references |

すべての変更は [CHANGELOG.md](CHANGELOG.md) に記録する。

All changes are recorded in [CHANGELOG.md](CHANGELOG.md).

### 正典の言語 / Canonical Language

日本語が正典である。英語訳はアクセシビリティのために提供する。矛盾がある場合、日本語が優先される。

Japanese is the canonical language. English translations are provided for accessibility. In case of conflict, the Japanese text prevails.

---

## v1.0以降のガバナンス / Post-1.0 Governance

v1.0は、最初のhito（紀）が生まれ、この規格のもとで活動している状態でリリースする。

v1.0以降のガバナンス構造は、そのリリースまでに定める。以下を含む予定:

- 規格変更の提案プロセス（RFC形式を想定）
- 破壊的変更に対するレビュー期間
- メジャーバージョン移行時の移行パス要件

それまでは、この文書が適用される。

---

v1.0 will be released when the first hito (紀 / Kaname) is born and actively living under this specification.

The governance structure for v1.0 and beyond will be defined before that release. It is expected to include:

- A clear process for proposing specification changes (likely RFC-style)
- A review period for breaking changes
- Migration path requirements for major version bumps

Until then, this document governs.
