## System Architecture

The following diagram illustrates the data flow from the initial meeting recording through to task synchronization in project management tools.

```mermaid
graph TD
  %% Input Triggers & STT Layer
  A0[Meeting Audio/Video File] -->|OpenAI Whisper API| A1[Meeting Transcript]
  A1 --> B[main.py Kernel]
  A2[HEARTBEAT.md Trigger] -- "Interval: 15 Mins" --> B
    
  %% The Unified Brain
  B --> C{SOUL.md Reasoning}
  C --> D[Deduplication Skill]
  D --> E[n8n_handshake.py]
    
  %% Execution Layer
  E --> F[n8n Orchestrator]
  F --> G[Monday.com Task Sync]
  F --> I[Notion Dashboard]
