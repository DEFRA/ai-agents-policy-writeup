# Defra AI Agents in Policy Work: Technical Implementation Guide
Version 0.1

A comprehensive technical writeup documenting the design, implementation, and deployment of multi-agent AI systems for policy work at the UK Department for Environment, Food & Rural Affairs (Defra).

## Executive Summary

This document presents two sophisticated **multi-agent AI workflows** built using LangGraph that demonstrate advanced patterns in enterprise AI deployment for government policy work:

1. **Parliamentary Questions System** - 6-agent workflow processing parliamentary questions with semantic search, intelligent filtering, and automated quality assurance
2. **Letters Analysis System** - 11-agent workflow analysing government correspondence, extracting issues, conducting research, and generating policy responses

Both systems showcase **hybrid LLM architectures**, **progressive data refinement**, and **citation-driven research synthesis** while maintaining strict privacy, quality, and compliance requirements.

## Table of Contents
1. [Parliamentary Questions Agents](pages/parliamentary-questions-agents/README.md)
    1. [Search Agent](pages/parliamentary-questions-agents/search-agent.md)
    2. [Filter Agent](pages/parliamentary-questions-agents/filter-agent.md)
    3. [Key Elements Agent](pages/parliamentary-questions-agents/key-elements-agent.md)
    4. [Response Agent](pages/parliamentary-questions-agents/response-agent.md)
    5. [Review Agent](pages/parliamentary-questions-agents/review-agent.md)
    6. [JSON Formatter Agent](pages/parliamentary-questions-agents/json-formatter-agent.md)
2. [Parliamentary Questions Deployment](pages/parliamentary-questions-deployment/README.md)
    1. [Backend API](pages/parliamentary-questions-deployment/backend.md)
    2. [Frontend App](pages/parliamentary-questions-deployment/frontend.md)
3. [Letters Agents](pages/letters-agents/README.md)
    1. [Prompt Loading & Configuration](pages/letters-agents/prompt-loading-configuration.md)
    2. [Letter Summarization](pages/letters-agents/letter-summarization.md)
    3. [Issue Extraction](pages/letters-agents/issue-extraction.md)
    4. [Issue Parsing](pages/letters-agents/issue-parsing.md)
    5. [Keyword Extraction](pages/letters-agents/keyword-extraction.md)
    6. [Research Question Generation](pages/letters-agents/research-question-generation.md)
    7. [Question Prioritization](pages/letters-agents/question-prioritization.md)
    8. [Internet Research](pages/letters-agents/internet-research.md)
    9. [Answer Synthesis](pages/letters-agents/answer-synthesis.md)
    10. [Issue Research Summarization](pages/letters-agents/issue-research-summarization.md)
    11. [Government Response Generation](pages/letters-agents/government-response-generation.md)
4. [Appendix](pages/appendix/README.md)
    1. [Response Agent - Prompt Details](pages/appendix/response-agent-prompt-details.md)
    2. [Review Agent - Prompt Details](pages/appendix/review-agent-prompt-details.md)

## What We Built

### Parliamentary Questions Agent System
A production-ready AI workflow that processes queries about UK Parliamentary Questions and generates compliant, high-quality responses.

**Core Capabilities:**
- Semantic search across Parliamentary Question corpus using OpenAI embeddings
- Intelligent relevance filtering reducing results from 10 to 5 most contextual matches
- Parliamentary-standard response generation (150-200 words) with formal tone
- Automated quality assurance against 6 Parliamentary criteria
- Complete audit trail with iterative improvement cycles

### Letters Analysis Agent System  
A sophisticated research and response system that processes government correspondence and generates evidence-based policy responses.

**Core Capabilities:**
- Multi-stage letter analysis: summarisation → issue extraction → keyword identification
- Intelligent research question generation with combinatorial optimisation
- Automated internet research restricted to authoritative government sources
- Evidence synthesis with complete citation tracking
- Government-standard response generation with full provenance

## How It Works

### Architecture Philosophy: Hybrid Intelligence

Both systems implement a **hybrid LLM strategy** that balances privacy, capability, and cost through strategic model deployment:

- **Local models** handle sensitive data processing (privacy compliance, cost predictability)
- **Cloud models** perform complex reasoning on abstracted, non-sensitive data
- **Progressive abstraction** ensures sensitive details are systematically removed before external processing

### Technical Foundation: LangGraph State Machines

**Why LangGraph:**
- **State persistence** - Complete workflow state management with rollback capability
- **Conditional routing** - Dynamic workflow paths based on runtime conditions  
- **Error containment** - Individual agent failures don't propagate through the pipeline
- **Compositional design** - Complex workflows built from simple, reusable components

**Key Implementation Patterns:**
- Typed state management with automatic message handling
- Quality gates with iterative improvement loops (max 3 attempts)
- Comprehensive audit trails for debugging and compliance
- Graceful degradation when components fail

### Design Decisions and Rationale

#### 1. Progressive Data Refinement
**Decision:** Multi-stage transformation pipeline where each agent operates at higher abstraction levels
**Rationale:** Enables sophisticated analysis while maintaining privacy and quality control
**Implementation:** Raw text → structured summaries → discrete issues → research questions → evidence → responses

#### 2. Intelligent Question Prioritisation
**Decision:** Algorithmic filtering to reduce research operations from ~245 to ~25 per letter
**Rationale:** Prevents combinatorial explosion while maintaining comprehensive coverage
**Implementation:** Multi-objective optimisation balancing relevance, coverage, and resource constraints

#### 3. Citation-Driven Research
**Decision:** All research restricted to government domains with mandatory source attribution
**Rationale:** Ensures epistemological rigour and maintains institutional authority
**Implementation:** Government-only source filtering + immediate citation tracking + triangulation across multiple sources

#### 4. Quality Assurance Loops
**Decision:** Automated review cycles with iterative improvement (max 3 attempts)
**Rationale:** Ensures Parliamentary compliance while preventing infinite loops
**Implementation:** LLM-powered assessment against defined criteria + structured feedback + cumulative improvement

## Implementation Details

### Parliamentary Questions System
- **Search Agent** - OpenAI embeddings with local API integration
- **Filter Agent** - LLM-powered relevance assessment  
- **Key Elements Agent** - Structured information extraction
- **Response Agent** - Parliamentary-standard content generation
- **Review Agent** - 6-criteria compliance assessment
- **JSON Formatter** - Structured output with complete audit trail

### Letters Analysis System
- **Configuration Management** - Template-based prompt engineering
- **Analysis Pipeline** - Summarisation → issue extraction → parsing → keyword extraction
- **Research Pipeline** - Question generation → prioritisation → internet research → synthesis
- **Response Generation** - Evidence-based government response with full citations

### Quality Metrics and Compliance

**Parliamentary Standards Enforcement:**
- Language appropriateness (formal, neutral tone)
- Factual accuracy against official records
- Currency requirements (recent, relevant information)
- Length optimisation (150-200 words)
- Sensitivity handling for political topics

**Privacy and Security:**
- Information locality principle (process sensitive data locally)
- Progressive abstraction patterns
- Zero-trust data flow between processing stages
- Data minimisation across security boundaries

## Deployment Architecture

### Backend Infrastructure
[[CHECK DETAIL]] - *Backend deployment details need to be added when available*

### Frontend Applications  
[[CHECK DETAIL]] - *Frontend implementation details need to be added when available*


## Contact Us

The Defra AI Capabilities and Enablement team maintains this technical documentation. Contact us:

- Through the `#ask-ace` slack channel on Defra slack ("grey slack")
- Via Steve Dickinson, Principal Software Developer (CCTS AI and Innovation)

## Contributing

We welcome contributions from the Defra community. See the [CONTRIBUTING](pages/appendix/CONTRIBUTING.md) file for how to contribute to this documentation.
