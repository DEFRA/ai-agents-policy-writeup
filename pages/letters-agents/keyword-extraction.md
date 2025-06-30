---
layout: default
title: Keyword Extraction Agent
parent: Government Letter Analysis: Multi-Agent AI Pipeline
---

# Keyword Extraction: Cloud-Based Policy Analysis Agent

## Overview

The keyword extraction agent marks the critical transition from privacy-constrained local processing to cloud-based intelligence. Each policy issue receives focused analysis from a specialized AI agent to extract relevant policy keywords.

**Pipeline Position**: Issues → Keywords → Research Questions  
**Processing Model**: Cloud-based (OpenAI GPT-4o-mini)  
**Architecture Pattern**: Granular agent specialization  

## Design Decisions

### Privacy Boundary Transition

**Decision**: Transition from local to cloud processing at this stage

**Rationale**: 
- Data has been sufficiently abstracted through summarization and issue extraction
- Personal information removed during previous issue extraction stage
- Content now focuses on general policy concerns rather than specific individuals
- Abstracted data meets compliance requirements for external processing

**Risk Mitigation**: Raw letter content never reaches cloud services - only abstracted policy issues

### Granular Agent Specialization Pattern

**Decision**: Process each issue individually with separate AI calls

**Rationale**:
- **Focused attention**: Each issue receives undivided AI analysis
- **Error isolation**: Problems with one issue don't affect others  
- **Context optimization**: Tailored prompts for specific issue characteristics
- **Quality maximization**: Full LLM attention per issue
- **Parallel processing**: Architecture supports future concurrent enhancement

**Trade-offs**:
- Higher API costs vs batch processing
- Sequential processing vs potential speed gains from batching

### Cloud Model Selection

**Decision**: Use OpenAI GPT-4o-mini

**Rationale**:
- **Capability**: Advanced reasoning superior to local models for policy analysis
- **Cost efficiency**: Mini variant balances capability with cost for focused tasks
- **Consistency**: Lower temperature settings ensure reproducible results
- **Government requirements**: Reliable performance for policy applications

## Implementation Details

### Input Processing

**Data Flow**:
```
Issue Object → Context Construction → AI Analysis → Keyword Extraction → Validation
```

**Context Construction** for each AI call:
- Letter summary for broader understanding
- Specific issue details across all [five dimensions](issue-extraction.md#five-dimensional-issue-model)
- Issue type and characteristics
- Optimized formatting for analysis quality

### Prompt Engineering

**Role-Based Instructions**:
- Establishes AI as expert policy analyst
- Specializes in identifying key concepts for government response preparation
- Clear guidelines for policy relevance and substance capture
- Structured output format requirements

**Template Structure**:
```markdown
You are an expert policy analyst specializing in [domain].
Analyze this issue: [issue_details]
Extract 3-5 policy-relevant keywords that would help government staff prepare responses.
Format: **Keyword**: Explanation of policy relevance
```

**Quality Standards**:
- Keywords must be directly relevant to policy formulation
- Each keyword requires explanation of government relevance
- Focus on actionable concepts for response preparation
- Avoid generic terms - select specific, meaningful concepts

### Output Processing and Validation

**Parsing Logic**:
- Handles multiple output format variations from LLM
- Extracts keyword-explanation pairs using regex patterns
- Validates minimum content requirements
- Ensures meaningful explanations accompany each term

**Quality Validation Framework**:
- Minimum content length requirements
- Policy relevance indicators
- Explanation quality assessment  
- Government application suitability check

**Data Structure**:
```python
KeywordObject = {
    'keyword': str,           # The policy term
    'explanation': str,       # Relevance explanation  
    'issue_id': str,          # Source issue reference
    'quality_score': float,   # Validation metrics
    'raw_output': str         # Original LLM response for debugging
}
```

## Error Handling and Quality Assurance

### Individual Issue Error Isolation

**Strategy**: Each issue processes independently with isolated error handling

**Benefits**:
- Pipeline continues with successful results even if some issues fail
- Complete error tracking for analysis and improvement  
- Graceful degradation prioritizes partial success over complete failure
- Comprehensive logging enables systematic optimization

**Error Categories**:
- API failures (timeout, rate limits)
- Parsing failures (unexpected output format)
- Validation failures (low-quality keywords)

### Quality Metrics

**Success Tracking**:
- Keyword extraction success rate per issue
- Quality validation pass rates
- Average keywords per successful issue
- Error distribution analysis

**Quality Indicators**:
- Policy relevance scores
- Explanation completeness
- Actionability assessment
- Government staff feedback integration

## Integration Architecture

### Upstream Integration (Issue Parsing)

**Input Requirements**:
- Structured issue objects with complete metadata
- Issue categorization and priority indicators
- Relationship tracking to original letter content

### Downstream Integration (Research Question Generation)

**Output Handoff**:
- Successfully extracted keywords become input for research question generation
- Rich metadata preserved through pipeline transition
- Error state tracking enables intelligent downstream processing
- Quality indicators guide research question prioritization

**Data Flow Continuity**:
```
Issues → [Keyword Extraction] → Keyword Objects → Research Question Generation
```

## Rationale and Benefits

### Intelligence Amplification

**Cloud Capability Advantages**:
- Sophisticated policy analysis beyond local model capabilities
- Broader knowledge synthesis for government domain expertise
- Consistent, reproducible keyword identification
- Advanced reasoning for complex policy concept extraction

### Government Application Benefits

**Operational Impact**:
- **Scalable policy analysis**: Handle high volumes of citizen correspondence
- **Compliance maintenance**: Privacy requirements met through abstraction
- **Audit trails**: Complete traceability for accountability
- **Evidence-based decisions**: Quality keywords support informed policy responses

**Human Workflow Integration**:
- Keywords provide starting points for policy staff analysis
- Explanations offer context for non-domain experts
- Quality indicators guide human review priorities
- Error tracking enables continuous system improvement

---

**Previous Stage**: [Issue Parsing](issue-parsing.md)  
**Next Stage**: [Research Question Generation](research-question-generation.md) 