# Clarity Toolkit for Claude

[한국어 README](README.ko.md)

Four conversation skills for Claude: clarify an idea through an interview, prepare questions for someone who holds the answers, turn a draft into standalone final text, and hand work over to the next person or session.

| Skill | Use it when |
| --- | --- |
| `grill-me` | You have an idea or plan but have not worked out the requirements. |
| `to-question` | An expert, vendor, customer, or colleague holds facts or decisions you need. |
| `meta-conv-filter` | A draft revised in the conversation must make sense to someone who never saw that conversation. |
| `handoff` | Work continues with another person, agent, or a new session, or you are resuming from a handoff. |

Each skill moves Claude away from a default habit: Claude tends to start building instead of interviewing, to ask you the recipient's questions instead of drafting a questionnaire for them, to leave references such as "as discussed" in final text, and to blur proposed plans with completed work. Re-explaining (`wait-what`) is covered by Claude's ordinary behavior and is not included.

## Install

### Claude app (claude.ai)

Save each `skills/<name>/SKILL.md` as a skill in your Claude settings, or paste this into a conversation where Claude can read GitHub and propose skills:

> https://github.com/steves460ng/clarity-toolkit-claude
> Read the four SKILL.md files under `skills/` and propose them as skills so I can save them. If a skill with the same name already exists, update it instead of creating a duplicate.

### Claude Code

```
/plugin marketplace add steves460ng/clarity-toolkit-claude
/plugin install clarity-toolkit@clarity-toolkit-claude
```

## Usage

Ask in natural language. Naming the skill makes the choice explicit.

### grill-me — Clarify requirements through an interview

> Use grill-me to interview me. I want to build an onboarding page for new employees.

Claude asks one or two open questions per round, starting with prerequisite decisions (who the users are before how they log in). Answer in prose or by question ID, skip a question, or rewrite it. Say "stop here and summarize" at any time.

**What you get:** a summary of the goal, main users, scope, accepted decisions, constraints, and open questions. Confirming the summary does not authorize implementation.

### to-question — Prepare questions for someone else

> Use to-question to draft questions for an external payment provider. The recipient is a technical contact we are working with for the first time. We need to confirm recurring payment support, integration requirements, and the settlement schedule.

Claude drafts the document instead of asking you questions you cannot answer yourself. It asks at most two short questions first, and only when the recipient or the purpose is unclear. High-impact questions come first, each with a blank answer field. Deadlines and names are never invented. The questionnaire can be in a different language from the conversation.

**What you get:** a questionnaire with its purpose, recipient, context, answering instructions, and grouped questions. Claude drafts it but does not send it.

### meta-conv-filter — Make text stand on its own

> Use meta-conv-filter to make this plan readable without our conversation.

Removes revision traces ("improved version") and conversation references ("as discussed"), and replaces pointers such as "option two" with the actual decision. Missing information is marked as not specified rather than invented. Facts, numbers, uncertainty, and sources are kept.

**What you get:** the cleaned text itself, without a preface about what was removed.

### handoff — Pass the work on

> Use handoff to summarize this conversation. The next session will start with the mobile screen design.

Separates confirmed decisions, completed work with evidence, proposals, open questions, and next actions. Passwords and tokens are replaced with `[REDACTED]`. When you paste a handoff into a new conversation, Claude treats it as context to verify, not as proof of current state.

**What you get:** a handoff document the next person or session can continue from. Claude does not remember earlier conversations on its own; carry the handoff over yourself.

## Use them together

1. Clarify the idea with `grill-me`.
2. Put questions that need someone else's input into a document with `to-question`.
3. Turn the summary or resulting draft into final text with `meta-conv-filter`.
4. Pass the work on with `handoff`.

## Output

Interview rounds appear in the chat. Summaries, questionnaires, final text, and handoffs are created as an editable document when the session supports it; otherwise they come as one copyable Markdown block. A `.md` file is created only on request.

## License and attribution

MIT License. `grill-me`, `to-question`, and `handoff` are adapted from [Matt Pocock's skills](https://github.com/mattpocock/skills) via [Clarity Toolkit](https://github.com/steves460ng/clarity-toolkit); `meta-conv-filter` is original to Clarity Toolkit. See [LICENSE](LICENSE) and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

This project is not affiliated with or endorsed by Matt Pocock or Anthropic.
