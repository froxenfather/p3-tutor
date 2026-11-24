# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic engineering)](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Primary source on context as a finite resource, context rot, just-in-time retrieval, compaction, note-taking and sub-agents. Use for: what to keep in context, memory design, sub-agent trade-offs.
- [Docs: "Context windows" (Claude Platform docs)](https://platform.claude.com/docs/en/build-with-claude/context-windows)
  What counts toward the window and how tokens accumulate across turns. Use for: token counting and cost reasoning.
- [Paper: "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks" (Lewis et al., 2020)](https://arxiv.org/abs/2005.11401)
  The original retrieval-augmented generation paper. Use for: the origin of the retrieve-then-generate recipe.

## Wisdom (Communities)

- Local: the learner's design team and course staff
  Use for: whiteboard reviews of the assistant's context for one request.

## Gaps

- A high-trust, practical source on chunking manuals and evaluating retrieval quality.
