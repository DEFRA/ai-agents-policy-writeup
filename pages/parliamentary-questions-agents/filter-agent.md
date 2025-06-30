---
layout: default
title: Filter Agent
parent: Parliamentary Questions Agentic Workflow
---

# Filter Agent

## Overview

The Filter Agent reduces semantic search results to only the most relevant Parliamentary Questions using LLM-powered relevance assessment. It serves as an intelligent quality gate that eliminates tangentially related content through sophisticated reasoning about Parliamentary context and user intent.

**Input**: 10 search results from Search Agent  
**Output**: All relevant results (typically 3-7) with quality metadata  
**Purpose**: Improve response quality by eliminating irrelevant sources and concentrating processing on valuable content

## Design Decisions

### Why LLM-Powered Filtering Over Algorithmic Approaches?

**Algorithmic Limitations**:
- Vector similarity identifies related content but misses contextual relevance
- Surface-level matching focuses on statistical patterns rather than meaning
- Cannot understand nuanced relationships between policies and implications
- Static rules cannot adapt to novel query patterns

**LLM Advantages**:
- Understands intent behind user queries and content relationships
- Evaluates relevance based on meaning, not just similarity scores
- Handles novel situations and complex Parliamentary relationships
- Distinguishes between superficial and substantive relevance

### Why Filter Rather Than Use All Results?

**Semantic Search Limitations**: Semantic search identifies content that is contextually similar to the query but cannot determine actual relevance for answering the specific question. Similar topics may not provide useful information for the user's particular needs.

**Benefits**:
- **Cognitive Load Management**: Reduces processing burden on downstream agents
- **Quality Concentration**: Focuses attention on highest-quality sources  
- **Response Coherence**: Prevents fragmented responses from competing sources
- **Processing Efficiency**: Optimises speed without sacrificing quality

## Implementation Details

### Core Prompt Architecture

The agent operates with a **relevance assessment mission** using these specific criteria:

1. **Relevance**: Direct assessment of whether result addresses the user's question
2. **Topic Alignment**: Verification that result covers the same general topic/domain  
3. **Information Value**: Evaluation of whether result helps build a quality answer
4. **Context Utility**: Assessment of whether result provides helpful background

**Quality Guidelines**:
- Be moderately selective (semantic similarity often indicates genuine relevance)
- Include partial answers that provide useful context
- Consider synthesis potential from multiple related results
- Select all results that meet relevance criteria

**Response Format**: Simple binary decisions ("RELEVANT" or "IRRELEVANT") with no explanations required for downstream parsing.

### Assessment Framework

**Multi-Dimensional Evaluation**:
- **Direct Relevance**: Query intent matching and topic alignment
- **Quality Assessment**: Source authority, information completeness, factual accuracy
- **Temporal Analysis**: Currency evaluation with historical context preservation
- **Parliamentary Context**: Appropriateness for formal governmental communication



### Technical Architecture

**Model Requirements**:
- Advanced language understanding for governmental texts
- Complex logical reasoning capabilities about relevance
- Sufficient context window for multiple result evaluation
- Consistent assessment criteria across queries

**Processing Strategy**:
- Batch assessment of multiple results for consistency
- Parallel reasoning for concurrent evaluation
- Structured output for downstream compatibility

## Rationale

### Quality vs Quantity Trade-off

**Signal-to-Noise Improvement**: Eliminates marginally relevant results that degrade response quality while preserving substantive content that contributes meaningfully to responses.

**Downstream Optimisation**: Reduces cognitive load on subsequent agents, improves decision-making quality, and concentrates computational resources on most promising information.

### Parliamentary Context Specialisation

**Contextual Understanding**: The agent comprehends Parliamentary Question standards, formal language requirements, and governmental communication contexts that algorithmic approaches cannot match.

**Adaptive Assessment**: Handles the unique characteristics of Parliamentary content including policy evolution, departmental jurisdictions, and political sensitivities.

## Error Handling

### Edge Cases

**Insufficient Quality Results**:
- **Scenario**: All 10 search results are poor quality or irrelevant
- **Response**: Return best available results with quality warnings
- **Rationale**: Maintain workflow completion while signaling quality concerns

**Ambiguous Relevance**:
- **Scenario**: Results have mixed relevance with unclear assessment
- **Response**: Apply conservative retention with quality metadata
- **Rationale**: Preserve potentially useful information while flagging uncertainty

### Quality Assurance

**Consistency Enforcement**:
- Standardised criteria application across all queries
- Bias mitigation approaches
- Minimum quality thresholds for result retention

**Error Prevention**:
- Over-filtering protection safeguards
- Under-filtering detection mechanisms
- Context preservation checks

## Integration

### Input Processing
**Format**: 10 search results with similarity scores and metadata from Search Agent  
**Validation**: Ensures result structure meets filtering requirements  
**Context**: Maintains user query context throughout assessment

### Output Generation
**Format**: All relevant results with enhanced metadata  
**Metadata**: Relevance confidence scores and assessment rationale  
**Compatibility**: Structured format optimised for Key Elements Agent consumption

### State Management
```python
# LangGraph state updates
filtered_results: List[Dict[str, Any]]  # All relevant results
quality_metadata: Dict[str, Any]        # Assessment confidence and rationale
```

## Performance Metrics

**Quality Indicators**:
- Filtering accuracy (how well filtered results support quality responses)
- Relevance precision (percentage of retained results that prove useful)
- Coverage completeness (ensuring important query aspects aren't lost)

**Efficiency Measures**:
- Processing time per result assessment
- Consistency across similar queries
- Downstream agent processing improvements 