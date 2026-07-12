# MemoryPlugin tool reference

Tool names below are the bare names; your client may prefix them (for example `mcp__memoryplugin__store_memory`).

## Memories (the notebook)

| Tool | Use for |
|---|---|
| `store_memory` | Save one atomic memory. Provide the text and, when known, the target bucket. |
| `search_memories` | Hybrid semantic plus keyword search over saved memories. First stop for recall. Accepts an optional bucket filter and result limit. |
| `get_memories_and_buckets` | Fetch recent or all memories, optionally by bucket, along with the bucket list. Good for a quick "what is here" scan. |
| `list_buckets` | List the user's buckets (topical folders). Check before storing so facts get filed correctly. |
| `create_bucket` | Create a new bucket. Only for a genuinely new long-lived topic. |
| `list_bucket_categories` | Smart Memory categories inside a bucket: each has a summary and guidance on when to load more. Cheap broad orientation. |
| `list_category_memories` | Load the full memories of one category, after its summary proved relevant. |
| `update_or_move_memories` | Edit a memory's text or move it between buckets. Use to fix facts that were always wrong. |

## Chat history (the archive)

| Tool | Use for |
|---|---|
| `recall_chat_history` | Search the user's imported past conversations across AI tools. Use when the user references an earlier discussion, wherever it happened. Supports a `queries` array for parallel multi-angle recall, per-query token budgets (roughly 300 to 1000), `before`/`after` date bounds, and a slower quality mode for hard queries. |
| `chat_history_overview` | Summary of what chat history exists (sources, volume, time range). |
| `get_conversation_summary` | Summary of one past conversation found via recall. |
| `get_full_conversation` | Full transcript of one past conversation. Use sparingly, transcripts can be long. |
| `export_conversation` | Temporary download link (expires in 15 minutes, no login needed) for one past conversation as a JSON file. Use when the user wants to save a chat as a file; to read content, use `get_full_conversation` instead. |
| `search_uploaded_files` | Search files the user uploaded to MemoryPlugin. |

## Calling patterns

- Recall: `search_memories` with concrete nouns; 1 or 2 calls, then work. Broad orientation: `list_buckets` then `list_bucket_categories`, then `list_category_memories` only where relevant.
- Store: `list_buckets` (if not already known this session), then `store_memory` per atomic fact.
- Cross-tool history: `recall_chat_history` (fan out with the `queries` array on multifaceted topics), then `get_conversation_summary` on promising sources, then `get_full_conversation` only if needed. When the user wants a chat saved as a file, hand them the link from `export_conversation`.
