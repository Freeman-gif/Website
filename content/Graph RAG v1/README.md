# Graph RAG v1 — NGSS Knowledge Base Extraction

Auto-generated Obsidian knowledge base from NGSS-related PDF documents using **Microsoft GraphRAG** for entity extraction and community detection.

## Method Overview

```mermaid
graph TD
    subgraph "Phase 1: Document Preparation"
        A["25 NGSS PDF Documents<br>(standards, research papers,<br>assessment guides)"] --> B["PyMuPDF text extraction<br>(PDF → .txt)"]
    end

    subgraph "Phase 2: GraphRAG Indexing (one-time LLM cost)"
        B --> C["Text Chunking<br>1200 chars, 100 overlap"]
        C --> D["Entity Extraction<br>gpt-4o-mini reads each chunk,<br>identifies concepts & relationships"]
        D --> E["Graph Construction<br>Merge entities + relationships<br>into knowledge graph"]
        E --> F["Community Detection<br>Leiden algorithm clusters<br>related entities into topics"]
        F --> G["Community Summarization<br>gpt-4o-mini writes summaries<br>for each topic cluster"]
        E --> H["Embedding Generation<br>text-embedding-3-small<br>vectorizes entity descriptions"]
    end

    subgraph "Phase 3: Obsidian Export"
        D --> I["entities.parquet"]
        E --> J["relationships.parquet"]
        G --> K["community_reports.parquet"]
        I --> L["Classify entities into categories<br>(standards, practices, DCIs,<br>CCCs, papers, grade_bands)"]
        L --> M["Generate Obsidian notes<br>YAML frontmatter +<br>content + backlinks"]
        J --> M
        K --> N["Generate community<br>summary notes"]
    end

    subgraph "Phase 4: Knowledge Base Output"
        M --> O["knowledge_base/"]
        N --> O
        O --> P["standards/"]
        O --> Q["practices/"]
        O --> R["crosscutting_concepts/"]
        O --> S["disciplinary_core_ideas/"]
        O --> T["papers/"]
        O --> U["grade_bands/"]
        O --> V["communities/"]
    end

    style A fill:#e1f5fe
    style O fill:#e8f5e9
```

## Models Used

| Component | Model | Provider | Purpose |
|-----------|-------|----------|---------|
| Entity Extraction | `gpt-4o-mini` | Azure OpenAI | Reads text chunks, identifies entities (concepts, standards, people, organizations) and relationships between them |
| Community Summarization | `gpt-4o-mini` | Azure OpenAI | Writes thematic summaries for each cluster of related entities |
| Embeddings | `text-embedding-3-small` | Azure OpenAI | Generates vector representations of entity descriptions for similarity search |

**Azure OpenAI Resource**: `ngss-api` (endpoint: `https://ngss-api.openai.azure.com`)

## GraphRAG Configuration

| Setting | Value | Rationale |
|---------|-------|-----------|
| Chunk size | 1200 characters | Balance between granularity and cost |
| Chunk overlap | 100 characters | Prevents losing context at chunk boundaries |
| Max gleanings | 1 | Additional extraction passes per chunk |
| Community max cluster size | 10 | Keeps topic groups focused |
| Community report max length | 2000 tokens | Detailed but not overly long summaries |

## Pipeline Architecture

```mermaid
graph LR
    subgraph "Indexing Pipeline (graphrag index)"
        direction TB
        W1["load_input_documents"] --> W2["create_base_text_units"]
        W2 --> W3["create_final_documents"]
        W3 --> W4["extract_graph"]
        W4 --> W5["finalize_graph"]
        W5 --> W6["create_communities"]
        W6 --> W7["create_final_text_units"]
        W7 --> W8["create_community_reports"]
        W8 --> W9["generate_text_embeddings"]
    end
```

```mermaid
graph LR
    subgraph "Query Pipeline (graphrag query)"
        direction TB
        Q1["User question"] --> Q2{"Search method"}
        Q2 -->|"Local (-m local)"| Q3["Find relevant entities<br>+ walk graph neighborhood"]
        Q2 -->|"Global (-m global)"| Q4["Read community summaries<br>+ synthesize themes"]
        Q3 --> Q5["LLM generates answer<br>with entity context"]
        Q4 --> Q5
    end
```

## Obsidian Note Format

Each generated note follows this structure for compatibility with the custom GraphRAG parser in `data_pipeline/graphrag/parser.py`:

```markdown
---
category: disciplinary_core_ideas
type: concept
source: graphrag_extraction
extracted_date: 2026-02-28
---

# PS2.B: Types of Interactions

## Description

Gravitational forces are always attractive and depend on
the masses of interacting objects...

## Related Concepts

- [[MS-PS2-4]] — Students construct arguments about gravitational interactions
- [[Engaging in Argument from Evidence]] — Primary SEP for this PE
- [[Systems and System Models]] — Related crosscutting concept
- [[How People Learn]] — Research on force misconceptions
```

The YAML frontmatter is parsed by the custom GraphRAG system to categorize nodes, and `[[backlinks]]` are extracted to build graph edges.

## Entity Classification

Entities extracted by GraphRAG are automatically classified into Obsidian categories using keyword matching:

```mermaid
graph TD
    E["GraphRAG Entity"] --> C{"Classify by title,<br>type, description"}
    C -->|"PE codes (MS-PS2-4, K-ESS3-1)"| S["standards/"]
    C -->|"SEP keywords (Engaging in Argument,<br>Developing Models)"| P["practices/"]
    C -->|"CCC keywords (Cause and Effect,<br>Systems and System Models)"| CC["crosscutting_concepts/"]
    C -->|"DCI codes (PS2, LS1, ESS2)<br>or domain keywords"| D["disciplinary_core_ideas/"]
    C -->|"Document types (report,<br>framework, study)"| R["papers/"]
    C -->|"Grade keywords (K-2, 6-8,<br>elementary, middle)"| G["grade_bands/"]
    C -->|"No match"| GN["general/"]
```

## Source Documents

25 PDF documents from the NGSS research collection:

- NGSS framework and standards documents
- ELA/ELD standards and integration guides
- Learning science research (How People Learn, etc.)
- Assessment framework and design guides (SNAP, NAEP, NSTA)
- ELL support and language integration research
- Curriculum design toolkits

## Integration with DCI Unpacking Pipeline

The generated knowledge base plugs into the existing ADAPT AI pipeline:

```mermaid
graph LR
    KB["Graph RAG v1<br>knowledge_base/"] --> PARSER["parser.py<br>(YAML + backlinks)"]
    PARSER --> GRAPH["graph.py<br>(in-memory graph)"]
    GRAPH --> QUERY["query.py<br>(traversal + filtering)"]
    QUERY --> PROVIDER["p1_provider.py<br>(enriches Generator context)"]
    PROVIDER --> GEN["Generator Agent<br>(DCI unpacking)"]
```

To connect:
```bash
# Set environment variable
export KNOWLEDGE_BASE_PATH="/Users/freeman/Desktop/ED_PhD_Project/ED_Project/Graph RAG v1/knowledge_base"
```

Or uncomment the GraphRAG code in `data_pipeline/providers/p1_provider.py`.

## Notebooks

| Notebook | Location | Purpose |
|----------|----------|---------|
| `test_graphrag.ipynb` | `azure-backend/tests/` | PDF extraction, GraphRAG indexing, query testing |
| `extract_graphrag.ipynb` | `azure-backend/tests/` | Export parquet → Obsidian notes |

## Reproducibility

To regenerate the knowledge base from scratch:

1. Run `test_graphrag.ipynb` cells 1-6 (extract PDFs, configure Azure OpenAI, run indexing)
2. Run `extract_graphrag.ipynb` (export to Obsidian notes)
3. Open this folder as an Obsidian vault to browse and refine
