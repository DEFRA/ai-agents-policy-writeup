---
layout: default
title: Search Agent
parent: Parliamentary Questions Agentic Workflow
---

# Search Agent

## Overview

The Search Agent is the first component in our Parliamentary Questions agentic workflow. It performs semantic discovery of relevant Parliamentary Questions from the corpus using vector-based similarity matching.

**Core Function**: Retrieves the 10 most semantically relevant Parliamentary Questions for any given user query, providing the factual foundation for all downstream processing.

**Key Characteristic**: This agent uses **direct API integration** rather than LLM prompts - it operates as a pure HTTP client rather than an AI reasoning agent.

## Design Decisions

### Why No LLM Prompts?

The Search Agent operates through **programmatic API integration** rather than natural language instructions because:

- **Performance**: Direct HTTP calls avoid LLM processing overhead
- **Reliability**: Deterministic behavior without language model variability  
- **Scalability**: High-throughput processing with minimal computational requirements
- **Separation of Concerns**: Pure data retrieval vs. reasoning functionality

### Why Semantic Search Over Traditional Methods?

**Traditional Search Limitations**:
- Keyword matching fails with formal Parliamentary language vs. colloquial queries
- Boolean queries miss semantically similar but lexically different content
- Cannot understand policy relationships and thematic connections

**Semantic Search Advantages**:
- Vector embeddings capture meaning beyond literal word matching
- Handles formal Parliamentary language vs. informal user queries
- Understands policy connections and provides ranked similarity scores

### Why External API Architecture?

We implemented search as an external service rather than embedded functionality for:

- **Computational Isolation**: Vector operations are resource-intensive and benefit from dedicated infrastructure
- **Independent Scaling**: Search service scales separately from agent workflow
- **Technology Flexibility**: Search implementation can be optimized/replaced without affecting agents [[CHECK DETAIL: Are there specific performance benchmarks that drove this decision?]]
- **Reusability**: Multiple applications can leverage the same search infrastructure

## Implementation Details

### Vector Embedding Process

**Technology**: OpenAI `text-embedding-3-small` model for high-quality semantic representations

**Process Flow**:
1. **Query Vectorization**: User query → high-dimensional vector representation (1536 dimensions)
2. **Corpus Comparison**: Query vector compared against pre-computed Parliamentary Question embeddings  
3. **Similarity Ranking**: Cosine similarity scores determine relevance
4. **Top-K Selection**: Return 10 most semantically similar questions (no threshold filtering)

**Why 10 Results?**: Provides sufficient candidates for downstream filtering while maintaining processing efficiency and preventing cognitive overload.

### Agent Behavior Definition

**HTTP Request Configuration**:
```
Endpoint: localhost:8000/search/questions
Method: GET
Parameters: query, limit (default: 10), split_text
Response: JSON with question text, metadata, similarity scores
```

**Processing Logic**:
1. Extract latest user message from conversation history
2. Sanitize query for API consumption
3. Execute HTTP GET request
4. Parse and validate JSON response
5. Return structured results for downstream processing

### Technical Implementation

**Request Structure**:
- **Query Parameter**: Natural language question from user
- **Limit Parameter**: Configurable result count (default: 10)
- **Response Format**: Structured JSON with question text, metadata, similarity scores

**Quality Assurance**:
- Input validation before API calls
- Response structure verification  
- Comprehensive error logging
- Graceful degradation with empty result sets

## Error Handling & Resilience

### Failure Scenarios & Responses

| Scenario | Response | Rationale |
|----------|----------|-----------|
| API service unavailable | Return empty result set, log error | Allow workflow to continue with degraded functionality |
| Invalid/empty queries | Attempt search with sanitized query or return empty results | Prevent cascading failures |
| Network timeouts | Configurable timeout with empty result fallback | Ensure predictable response times |

### Recovery Mechanisms

- **Graceful Degradation**: System continues operation with empty results rather than complete failure
- **Error Logging**: Comprehensive error tracking for debugging
- **Timeout Management**: Prevents workflow blocking on slow operations

## Performance & Scalability

### Performance Characteristics

- **Vector Search Efficiency**: Pre-computed embeddings enable fast similarity calculations
- **Network Optimization**: Local API deployment minimizes latency
- **Parallel Processing**: Multiple search requests handled concurrently

### Scalability Features

- **Horizontal Scaling**: External API supports multiple service instances
- **Load Distribution**: Search load balanced across infrastructure
- **Resource Isolation**: Search operations don't compete with agent processing
- **Independent Optimization**: Search service optimized separately

## Integration Points

### Input
- **Source**: Natural language user query from workflow initialization
- **Processing**: Extract and sanitize query from conversation history

### Output  
- **Format**: Structured JSON with metadata and similarity scores
- **Content**: Top 10 ranked results with Parliamentary session details, dates, reference numbers
- **Quality Indicators**: Relevance ranking, coverage breadth, temporal distribution

### Downstream Compatibility
- Consistent JSON structure for Filter Agent consumption
- Preserved metadata for audit trail requirements
- Similarity scores for intelligent filtering

## Quality Metrics

### Search Quality Assessment
- **Relevance Precision**: Percentage of results truly relevant to query
- **Coverage Completeness**: Ensuring important relevant questions aren't missed  
- **Diversity Balance**: Avoiding overly narrow result sets
- **Temporal Currency**: Including recent questions alongside historical context

### Result Validation
- Structure consistency across all results
- Complete metadata presence verification
- Top-10 selection without similarity threshold filtering
- Malformed result detection and handling