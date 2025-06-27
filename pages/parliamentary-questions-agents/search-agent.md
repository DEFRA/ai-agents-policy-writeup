---
layout: default
title: Search Agent
parent: Parliamentary Questions Agentic Workflow
---

# Search Agent

## Overview
The Search Agent serves as the foundational data retrieval layer in our Parliamentary Questions agentic workflow, responsible for semantic discovery of relevant Parliamentary Questions from the corpus using vector-based similarity matching.

## Agent Implementation Approach

### Why No LLM Prompts?
Unlike other agents in our workflow, the Search Agent **does not use LLM prompts** because it operates as a **pure API integration agent** rather than an LLM-powered reasoning agent. Its functionality is achieved through direct HTTP communication with external services rather than natural language instruction processing.

### Direct API Integration Method
The Search Agent's behavior is defined through:

**HTTP Request Configuration**:
- **Endpoint Definition**: Direct calls to localhost:8000/search/questions
- **Parameter Structure**: Query, limit, and split_text parameters
- **Request Format**: GET requests with URL parameters
- **Response Handling**: JSON parsing and validation

**Programmatic Logic**:
- **Query Extraction**: Systematic extraction of user queries from conversation history
- **API Call Execution**: Direct HTTP requests to semantic search service
- **Error Handling**: Graceful degradation when API unavailable
- **Result Validation**: Verification of response structure and content

**Configuration Parameters**:
- **Result Limits**: Configurable number of results (default: 10)
- **Text Splitting**: Configurable text processing parameters
- **Timeout Management**: Request timeout and retry logic
- **Error Recovery**: Fallback mechanisms for service failures

### Technical Implementation Details
The agent operates through **programmatic API integration** with the following characteristics:

**Request Processing**:
1. **Message Analysis**: Extract latest human message from conversation state
2. **Query Sanitization**: Clean and prepare query for API consumption
3. **API Communication**: Execute HTTP GET request with structured parameters
4. **Response Processing**: Parse JSON response and validate structure
5. **State Update**: Return structured results for downstream processing

**Quality Assurance**:
- **Input Validation**: Ensure valid queries before API calls
- **Response Verification**: Validate API response structure
- **Error Logging**: Comprehensive error tracking and reporting
- **Fallback Handling**: Graceful degradation with empty result sets

This **non-prompt approach** provides several advantages:
- **Performance Efficiency**: Direct API calls without LLM processing overhead
- **Reliability**: Deterministic behavior without language model variability
- **Scalability**: High-throughput processing capability
- **Resource Optimization**: Minimal computational requirements

## Technical Design Philosophy

### Why Semantic Search Over Traditional Methods?

**Problem with Traditional Approaches**:
- **Keyword Limitations**: Parliamentary language uses formal terminology that may not match colloquial user queries
- **Synonym Gaps**: Traditional search misses semantically similar but lexically different content
- **Context Blindness**: Keyword matching cannot understand policy relationships and thematic connections
- **Precision Issues**: Boolean queries return too many irrelevant results or miss relevant content

**Semantic Search Advantages**:
- **Conceptual Understanding**: Vector embeddings capture meaning beyond literal word matching
- **Linguistic Flexibility**: Handles formal Parliamentary language vs. informal user queries
- **Relationship Awareness**: Understands policy connections and thematic relationships
- **Scalable Relevance**: Provides ranked similarity scores for intelligent filtering

### Why External API Architecture?

**Design Decision Rationale**:
We implemented search as an external service rather than embedded functionality for several technical reasons:

**Separation of Concerns**:
- **Computational Isolation**: Vector search operations are resource-intensive and benefit from dedicated infrastructure
- **Scalability Independence**: Search service can scale independently of the agent workflow system
- **Technology Flexibility**: Search implementation can be optimized or replaced without affecting agent logic
- **Reusability**: Multiple applications can leverage the same search infrastructure

**Performance Optimization**:
- **Caching Strategies**: External service enables sophisticated caching of frequently accessed embeddings
- **Hardware Optimization**: Dedicated search infrastructure can use specialized hardware for vector operations
- **Load Distribution**: Search requests can be distributed across multiple service instances

## Primary Function
Performs semantic discovery of relevant Parliamentary Questions using OpenAI embeddings. Interfaces with local search API to retrieve top 10 most similar questions from the corpus, establishing the factual foundation for all downstream processing.

## Technical Implementation

### Vector Embedding Strategy

**Why OpenAI Embeddings?**:
- **High-Quality Representations**: OpenAI's embedding models provide state-of-the-art semantic representations
- **Parliamentary Language Optimization**: Training on diverse text corpora includes formal governmental language
- **Dimensional Efficiency**: Optimal balance between representational power and computational efficiency
- **Consistency**: Standardized embeddings ensure consistent similarity calculations across the corpus

**Embedding Process**:
1. **Query Vectorization**: User query is converted to high-dimensional vector representation
2. **Corpus Comparison**: Query vector is compared against pre-computed Parliamentary Question embeddings
3. **Similarity Ranking**: Cosine similarity scores determine relevance ranking
4. **Top-K Selection**: Retrieve the 10 most semantically similar questions

### API Integration Architecture

**HTTP-Based Communication**:
- **RESTful Design**: Standard HTTP GET requests with query parameters for broad compatibility
- **Stateless Operations**: Each search request is independent, enabling horizontal scaling
- **Error Resilience**: Graceful degradation when external service is unavailable
- **Timeout Management**: Prevents agent workflow blocking on slow search operations

**Request Structure**:
- **Query Parameter**: Natural language question from user
- **Limit Parameter**: Configurable result count (default: 10 for optimal filtering)

**Response Handling**:
- **Structured Results**: Consistent JSON format with question text, metadata, and similarity scores
- **Error Recovery**: Empty result sets trigger graceful downstream handling
- **Result Validation**: Ensures response structure meets agent workflow requirements

### Result Optimization Strategy

**Why 10 Results?**:
- **Filtering Buffer**: Provides sufficient candidates for intelligent downstream filtering
- **Quality vs. Quantity**: Balance between comprehensive coverage and processing efficiency
- **Cognitive Load Management**: Prevents overwhelming downstream agents with too many options
- **Performance Optimization**: Minimizes API response time while maximizing relevance potential

**Metadata Preservation**:
- **Source Information**: Parliamentary session details, question IDs, and reference numbers
- **Temporal Context**: Question dates and parliamentary period information
- **Similarity Scores**: Quantitative relevance measures for downstream processing
- **Question Classification**: Topic categories and departmental associations

## Key Features

### External API Integration
**Technical Implementation**: HTTP-based communication with local semantic search service
**Benefits**: Modular architecture, independent scaling, technology flexibility, reusable infrastructure

### Configurable Result Limiting
**Technical Implementation**: Parameterized result count with intelligent defaults
**Benefits**: Adaptable to different use cases, performance optimization, cognitive load management

### Error Handling and Recovery
**Technical Implementation**: Comprehensive exception handling with graceful degradation
**Benefits**: System resilience, predictable behavior, operational reliability

### Real-time Search Result Display
**Technical Implementation**: Configurable console output for development and debugging
**Benefits**: Workflow transparency, debugging support, development efficiency

### Foundational Data Provision
**Technical Implementation**: Structured result formatting for downstream agent consumption
**Benefits**: Consistent data structure, processing efficiency, agent interoperability

## Output Structure

### Structured Search Results
Each result contains:
- **Question Text**: Full Parliamentary Question content
- **Metadata**: Session information, dates, reference numbers
- **Similarity Scores**: Quantitative relevance measures
- **Source Information**: Parliamentary source and context
- **Timestamps**: Temporal context for currency assessment

### Quality Indicators
- **Relevance Ranking**: Ordered by semantic similarity scores
- **Coverage Breadth**: Diverse result set to capture different aspects of the query
- **Temporal Distribution**: Mix of recent and historical relevant questions
- **Departmental Diversity**: Results from multiple relevant government departments

## Error Recovery and Resilience

### API Failure Handling
**Scenario**: External search service unavailable or slow
**Response**: Return empty result set and log error for debugging
**Rationale**: Allow workflow to continue with degraded functionality rather than complete failure

### Invalid Query Handling
**Scenario**: Malformed or empty user queries
**Response**: Attempt search with sanitized query or return empty results
**Rationale**: Prevent cascading failures while maintaining workflow completion

### Network Timeout Management
**Scenario**: Slow network connections or overloaded search service
**Response**: Configurable timeout with empty result fallback
**Rationale**: Ensure predictable response times for API consumers

## Performance Characteristics

### Response Time Optimization
- **Vector Search Efficiency**: Pre-computed embeddings enable fast similarity calculations
- **Network Optimization**: Local API deployment minimizes latency
- **Caching Integration**: External service can implement sophisticated caching strategies
- **Parallel Processing**: Multiple search requests can be handled concurrently

### Scalability Considerations
- **Horizontal Scaling**: External API architecture supports multiple service instances
- **Load Distribution**: Search load can be balanced across infrastructure
- **Resource Isolation**: Search operations don't compete with agent processing resources
- **Independent Optimization**: Search service can be optimized independently

## Integration Points

### Upstream Integration
**Input**: Natural language user query from workflow initialization
**Processing**: Extract query from conversation history and sanitize for search
**Validation**: Ensure query is appropriate for semantic search processing

### Downstream Integration
**Output**: Structured search results with metadata and similarity scores
**Format**: Consistent JSON structure compatible with filter agent requirements
**Quality**: Ranked results with sufficient detail for relevance assessment

## Quality Assurance

### Search Quality Metrics
- **Relevance Precision**: Percentage of results that are truly relevant to the query
- **Coverage Completeness**: Ensuring important relevant questions are not missed
- **Diversity Balance**: Avoiding overly narrow result sets that miss broader context
- **Temporal Currency**: Including recent relevant questions alongside historical context

### Result Validation
- **Structure Consistency**: Ensuring all results conform to expected format
- **Content Completeness**: Verifying all essential metadata is present
- **Similarity Threshold**: Maintaining minimum relevance standards
- **Error Detection**: Identifying and handling malformed results

The Search Agent represents the critical foundation of our Parliamentary Questions analysis system, providing high-quality semantic discovery that enables all downstream processing. Its design emphasizes reliability, scalability, and integration flexibility while maintaining the semantic accuracy essential for Parliamentary Question analysis. 