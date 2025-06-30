---
layout: default
title: Parliamentary Questions Agentic Workflow
nav_order: 6
---

# Parliamentary Questions Agentic Workflow

## Executive Summary

This repository implements a sophisticated **multi-agent AI system** designed to process and answer queries about UK Parliamentary Questions using cutting-edge **LangGraph workflow orchestration**. The system combines semantic search, intelligent filtering, automated quality assurance, and Parliamentary standards compliance to deliver accurate, well-formatted responses.

## System Architecture

### Core Technologies
- **LangGraph**: Advanced workflow orchestration with conditional routing and state management
- **OpenAI Embeddings**: Semantic search capabilities for Parliamentary Question corpus
- **Multi-Agent Pipeline**: 6 specialized AI agents working in coordinated sequence
- **Quality Assurance Loop**: Automated Parliamentary review with feedback mechanisms
- **External API Integration**: RESTful semantic search service

## Agentic Workflow

### 1. **[Search Agent](search-agent.md)**
Performs semantic discovery of relevant Parliamentary Questions using OpenAI embeddings. Interfaces with local search API to retrieve top 10 most similar questions from the corpus.

### 2. **[Filter Agent](filter-agent.md)**
Applies LLM-powered relevance assessment to reduce search results from 10 to 5 most contextually relevant questions. Eliminates tangentially related or outdated information.

### 3. **[Key Elements Agent](key-elements-agent.md)**
Extracts critical themes, policies, stakeholders, and factual elements from filtered results. Provides structured foundation for comprehensive response generation.

### 4. **[Response Agent](response-agent.md)**
Generates Parliamentary-standard responses (150-200 words) using formal language and tone. Incorporates review feedback for iterative improvement across multiple attempts.

### 5. **[Review Agent](review-agent.md)**
Assesses responses against 6 Parliamentary criteria including appropriateness, currency, language, length, sensitivity, and readability. Provides pass/fail determination with specific improvement feedback.

### 6. **[JSON Formatter Agent](json-formatter-agent.md)**
Converts final response into structured JSON format including complete audit trail, search results, response attempts, and review feedback for API consumption.

## LangGraph Implementation

### State Management
The system uses **typed state management** through LangGraph's `StateGraph` with automatic message handling:

```python
class SimpleState(TypedDict):
    messages: Annotated[list, add_messages]  # Auto-managed conversation history
    search_results: List[Dict[str, Any]]     # Raw search results from API
    filtered_results: List[Dict[str, Any]]   # Relevance-filtered results
    key_elements: Optional[Dict[str, Any]]   # Extracted key information
    review_feedback: Optional[str]           # Parliamentary review feedback
    review_attempts: int                     # Loop prevention counter
    review_passed: bool                      # Quality gate status
    response_history: List[Dict[str, Any]]   # Complete attempt tracking
    feedback_history: List[str]              # All feedback provided
```

### Conditional Routing
**Dynamic workflow routing** based on review outcomes:
- **Pass**: Continue to JSON formatting
- **Fail + Attempts < 3**: Loop back to response generation with feedback
- **Fail + Max Attempts**: Proceed to output (prevents infinite loops)

### History Tracking
**Comprehensive audit trail** implementation:
- Every response attempt is recorded with timestamps and word counts
- All review feedback is tracked across improvement cycles
- Complete genealogy of response evolution
- Metadata preservation for debugging and quality analysis

## Parliamentary Standards Integration

### Compliance Framework
The system enforces strict **Parliamentary Question standards**:
- **Language Appropriateness**: Formal, respectful, politically neutral tone
- **Factual Accuracy**: Verification against official Parliamentary records
- **Currency Requirements**: Emphasis on recent and relevant information
- **Length Optimization**: 150-200 word responses for optimal readability
- **Sensitivity Handling**: Appropriate treatment of political and sensitive topics

### Review Methodology
- **Automated Assessment**: LLM-powered evaluation against all 6 criteria
- **Detailed Feedback**: Specific improvement suggestions for failed reviews
- **Iterative Improvement**: Up to 3 attempts with cumulative feedback integration
- **Pass/Fail Determination**: Clear binary outcomes with reasoning