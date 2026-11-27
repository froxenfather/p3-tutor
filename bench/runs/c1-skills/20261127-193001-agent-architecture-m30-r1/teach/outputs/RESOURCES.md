# Agent architecture Resources

## Knowledge

- [Article: "Effective context engineering for AI agents" (Anthropic engineering)](https://anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Primary source for O3. Use for: context rot, just-in-time retrieval, compaction, note-taking.
- [Docs: Context windows](https://platform.claude.com/docs/en/build-with-claude/context-windows)
  One provider's documentation. Use for: what counts toward the window, overflow behaviour.
- [Docs: Working with messages](https://platform.claude.com/docs/en/build-with-claude/working-with-messages)
  Use for: stateless requests and resending conversation history.
- [Docs: Glossary](https://platform.claude.com/docs/en/about-claude/glossary)
  Use for: definitions of token, context window, RAG.
- [Docs: Memory overview (LangChain)](https://docs.langchain.com/oss/python/concepts/memory)
  Use for: short-term vs long-term memory, kinds of memory, when to write.
- [Article: "Contextual retrieval" (Anthropic)](https://www.anthropic.com/news/contextual-retrieval)
  Use for: chunking, keyword plus embedding search, the lost-context problem.

## Wisdom (Communities)

- [Letta community forum](https://forum.letta.com/categories)
  Seen in search results, not yet reviewed in depth; centers on one framework. Use for: feedback on memory designs.
