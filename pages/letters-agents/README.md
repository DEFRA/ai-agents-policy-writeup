---
layout: default
title: Government Letter Analysis - Multi-Agent AI Pipeline
nav_order: 3
---

# Government Letter Analysis: Multi-Agent AI Pipeline

A LangGraph-based workflow that analyzes government correspondence using hybrid LLM architecture to balance privacy, capability, and cost constraints.

## Overview

**What it does:**
- Analyses government letters to extract key issues and policy concerns
- Researches policy context using government sources
- Generates comprehensive responses with full citations
- Maintains data privacy through hybrid local/cloud processing

**Key capabilities:**
- Processes sensitive government correspondence locally
- Intelligently prioritises research questions to avoid combinatorial explosion
- Restricts research to trusted government domains (.gov.uk, etc.)
- Provides full citation trails for all claims and recommendations

## Architecture

### Multi-Stage Processing Pipeline

```
1. Raw Letter        (Local)
   |
2. Summary           (Local) 
   |
3. Issues            (Local)
   |
4. Keywords          (Cloud)
   |
5. Questions         (Cloud)
   |
6. Research          (Cloud)
   |
7. Responses         (Cloud)
```

**Stage Details:**
1. **Text Processing (Local):** Extract summaries and identify discrete issues
2. **Keyword Extraction (Local):** Generate research keywords for each issue  
3. **Question Generation (Cloud):** Create specific research questions from keywords
4. **Question Prioritisation (Cloud):** Select optimal subset (~25 from ~245 potential questions)
5. **Research Execution (Cloud):** Search government sources for evidence
6. **Response Synthesis (Cloud):** Generate comprehensive answers with citations

### Hybrid LLM Strategy

**Local Models (Ollama):**
- **Purpose:** Process sensitive government correspondence
- **Rationale:** Ensures data privacy and sovereignty
- **Trade-offs:** Limited reasoning capability for basic text processing

**Cloud Models (OpenAI):**
- **Purpose:** Advanced reasoning on abstracted, non-sensitive data
- **Rationale:** Superior analytical capabilities for complex tasks
- **Input:** Only processed summaries and extracted keywords, never raw letters

## Design Decisions

### LangGraph State Machine Architecture

**Why LangGraph:**
- **State persistence:** Full workflow state preserved for debugging and analysis
- **Error isolation:** Agent failures contained without corrupting pipeline
- **Conditional routing:** Dynamic workflow paths based on runtime conditions
- **Transaction safety:** Each stage completes fully or rolls back cleanly

**Alternative considered:** Sequential function calls
**Decision rationale:** Complex multi-agent workflows require formal state management for reliability

### Intelligent Question Prioritisation

**Problem:** Without filtering, generates ~245 research questions per letter
**Solution:** Multi-objective optimisation to select ~25 high-value questions (10x reduction)

**Prioritisation criteria:**
- **Relevance:** Direct connection to identified issues
- **Coverage:** Balanced representation across all issues  
- **Specificity:** Concrete, answerable questions
- **Uniqueness:** Avoid redundant research paths

### Citation-Driven Research

**Source restrictions:** Only government domains (.gov.uk, official department sites)
**Rationale:** Institutional authority provides reliability for policy recommendations
**Implementation:** Every claim includes immediate source attribution

## Implementation Details

### Data Flow and Transformations

**Progressive abstraction pattern:**
- **Layer 1-3:** Raw text → Structured summaries → Discrete issues
- **Layer 4-6:** Issues → Keywords → Research questions
- **Layer 7-11:** Questions → Evidence → Synthesised responses

**State evolution:**
- Simple strings evolve into rich, interconnected data structures
- Each stage adds semantic richness while preserving previous information
- Maintains relationships between entities throughout pipeline

### Error Handling and Resilience

**ACID properties for AI workflows:**
- **Atomicity:** Each agent operation completes fully or not at all
- **Consistency:** State transitions maintain data structure invariants
- **Isolation:** Agent failures don't corrupt overall pipeline state  
- **Durability:** All transformations preserved for debugging

**Graceful degradation:** Partial failures result in reduced functionality rather than complete breakdown

### Prompt Engineering Architecture

**Template-based approach:**
- Markdown prompts with dynamic context injection
- Separation of prompt logic from application logic
- Configuration-driven behaviour modification

