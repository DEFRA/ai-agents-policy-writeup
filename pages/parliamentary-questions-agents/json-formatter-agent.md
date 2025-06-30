---
layout: default
title: JSON Formatter Agent
parent: Parliamentary Questions Agentic Workflow
---

# JSON Formatter Agent

## Overview

The JSON Formatter Agent is the final stage in our Parliamentary Questions workflow. It transforms approved responses and complete processing history into structured JSON output for API consumption.

**Core Function**: Convert workflow results into standardised JSON format with comprehensive audit trails and processing metadata.

## Design Decisions

### Why Final-Stage JSON Formatting?

**Separation of Concerns**: Processing logic remains separate from output formatting, allowing independent optimisation of each stage.

**API-First Design**: Structured output enables seamless integration with external systems and services.

**Audit Compliance**: Centralised formatting ensures consistent audit trail preservation across all responses.

### Why Comprehensive Audit Trails?

**Government Accountability**: Complete documentation of processing decisions for transparency and compliance.

**Quality Improvement**: Historical data enables system optimisation and pattern recognition.

**Debugging Support**: Detailed processing information facilitates troubleshooting and performance analysis.

## Implementation Details

### Input Processing

The agent receives complete workflow state including:
- Original user query
- Search results and filtering history
- Response generation attempts
- Parliamentary review assessments
- Processing metadata and timestamps

### Core JSON Schema

The agent enforces this exact schema structure:

```json
{
  "query": "<string>",
  "semantic_search": {
    "total_results": <integer>,
    "results": [
      {
        "id": "<string|integer>",
        "question": "<string>",
        "answer": "<string>",
        "score": <float>
      }
    ]
  },
  "key_information": ["<string>"],
  "final_answer": "<string>",
  "parliamentary_review": {
    "attempts": <integer>,
    "status": "<string>",
    "assessment": "<string>"
  }
}
```

### Processing Steps

1. **Extract Query**: Preserve original user question exactly as submitted
2. **Structure Search Results**: Convert raw search data to semantic_search format, maintaining original PQ IDs
3. **Distill Key Information**: Extract 3-5 key facts with PQ references and dates
4. **Format Final Answer**: Use AI response but remove PQ references (kept in key_information)
5. **Include Review Data**: Add attempt count, pass/fail status, and assessment details
6. **Generate JSON**: Create final structured output

### Critical Output Requirements

**Pure JSON Only**: 
- No markdown formatting or code blocks
- Direct JSON output from `{` to `}`
- Proper string escaping throughout

**Data Integrity**:
- Use actual PQ IDs from search results
- Preserve all original content accuracy
- Maintain British English spelling conventions

## Integration Architecture

### Workflow Position

```
[Response Agent] → [Review Agent] → [JSON Formatter Agent] → [API Output]
```

**Input**: Complete workflow state with all processing history
**Output**: API-ready JSON with embedded audit trail

### Consumer Support

**API Integration**: Standard REST API compatible JSON structure
**Schema Consistency**: Consistent field names and structure across outputs
**Documentation**: Self-describing JSON format with embedded metadata