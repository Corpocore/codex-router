- **Compaction now bounds images the same way a routed turn does.** The
  20MB / 128K-token image budget only ran on ordinary routed turns, so a
  screenshot-heavy conversation that reached auto-compaction sent every image
  it held to the summarizer. On OpenRouter that failed with `413 Downloaded
  image content cannot exceed 30MB`, and because Codex retries compaction
  before each following turn, the session could never take another turn.
  Compaction now turns the oldest images into text receipts before sending,
  keeps the newest two, and records the image counts on its usage event.
