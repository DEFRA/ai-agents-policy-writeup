---
layout: default
title: Response Agent
parent: Parliamentary Questions Agentic Workflow
---

# Response Agent

## Overview

The Response Agent generates Parliamentary-standard responses from structured information extracted by previous agents. It creates formal, 150-200 word responses that meet UK Government communication standards and incorporates iterative improvement based on quality assessment feedback.

**Core Function**: Transform structured Parliamentary data into formal governmental responses through iterative refinement.

## Architecture Decision: Dedicated Response Generation

### Why Separate Response Generation?
- **Specialisation**: Optimised specifically for Parliamentary language, tone and format standards
- **Cognitive Separation**: Isolates creative generation from critical assessment to reduce bias
- **Iterative Improvement**: Enables systematic enhancement through feedback loops
- **Quality Consistency**: Maintains uniform governmental communication standards

### Why Iterative Improvement?
- **Quality Optimisation**: Progressive enhancement through up to 3 attempts with targeted feedback
- **Failure Recovery**: Mechanism to improve substandard initial responses
- **Resource Balance**: Bounded iteration prevents excessive processing while allowing meaningful improvement
- **Empirical Limit**: 3 attempts provides sufficient opportunity for good answers; responses failing after 3 attempts typically require fundamental rework rather than incremental improvement

## Prompt Engineering Design

### Agent Persona
**Role**: Specialist policy writer in Defra's Circular Economy Policy team  
**Expertise**: Parliamentary Question response composition  
**Mandate**: Create formal, authoritative responses meeting Parliamentary standards

### Key Prompt Framework

**4-Step Process**:
1. **Review & Analysis**: Prioritise "Direct Answer - High" relevance elements, assess context and timeline
2. **Structure**: 3-part format (Opening statement, Multi-paragraph body, Closing action/next steps)
3. **Synthesis**: Formal Parliamentary language, no contractions, specific dates/figures, 200-300 words target
4. **Quality Check**: 4-point verification (Direct addressing, Evidence support, Language appropriateness, Completeness)

**Core Requirements**:
- **British English**: Spelling, grammar, vocabulary compliance
- **Formal Register**: Passive voice where appropriate, "The Government" not "We"
- **Prohibited Elements**: Contractions, speculation, citations/PQ numbers, rhetorical questions
- **Evidence-Based**: All facts must be supported by provided key elements
- **Comprehensive Coverage**: Address all aspects without leaving obvious follow-up questions

*See [Response Agent - Prompt Details](../appendix/response-agent-prompt-details.md) for complete implementation details.*

## Technical Implementation

### State Management
```python
# Key state elements for response generation
response_history: List[Dict[str, Any]]    # All attempts with metadata
feedback_history: List[str]               # Cumulative improvement guidance
review_attempts: int                      # Loop prevention counter
review_passed: bool                       # Quality gate status
```

### Iterative Improvement Architecture

**Attempt Flow**:
1. **Initial Generation**: Base response from structured key elements
2. **Review Integration**: Analyse Review Agent feedback for specific issues
3. **Targeted Enhancement**: Address feedback while preserving successful elements
4. **Quality Convergence**: Maximum 3 attempts to meet Parliamentary standards

**History-Aware Enhancement**:
- Complete awareness of previous attempts and their shortcomings
- Systematic incorporation of cumulative feedback
- Progressive quality improvement with audit trail

### Content Generation Process

**Information Synthesis**:
- **Key Elements Integration**: Themes, stakeholders, policies, facts from extraction phase
- **Priority Focus**: Emphasis on "Direct Answer - High" relevance items
- **Relationship Preservation**: Maintain connections between information elements
- **Context Weaving**: Coherent narrative from diverse sources

**Parliamentary Adaptation**:
- **Audience Targeting**: Parliamentary Question response conventions
- **Authority Positioning**: Appropriate governmental responsibility and authority
- **Stakeholder Sensitivity**: Balanced perspective acknowledgement

## Quality Standards

### Parliamentary Compliance Framework

**Language Standards**:
- Formal governmental tone with political neutrality
- Respectful terminology and diplomatic conventions
- Technical accuracy in Parliamentary/legal terminology
- British English throughout

**Content Requirements**:
- Comprehensive coverage of query aspects
- Factual accuracy from verified Parliamentary sources
- Current and relevant information with temporal context
- 150-200 word optimisation for Parliamentary conventions

**Format Specifications**:
- Clear introduction-body-conclusion structure
- Logical flow and idea connectivity
- Plain English principles within formal tone
- Accessibility for diverse audiences

### Assessment Integration

**Built-in Quality Awareness**:
- Anticipation of Parliamentary assessment criteria
- Preemptive improvement during generation
- Standards compliance preparation for review

## Integration Points

### Input Sources
- **Key Elements Agent**: Structured themes, stakeholders, policies, facts
- **User Query**: Original Parliamentary Question requiring response
- **Review Agent Feedback**: Specific improvement guidance (iterative attempts)

### Output Delivery
- **Primary**: Parliamentary-standard response (150-200 words)
- **Metadata**: Attempt history, improvement tracking, generation metadata
- **Quality Status**: Review readiness and standards compliance indicators

## Performance Characteristics

**Quality Metrics**:
- Parliamentary standards compliance rate by attempt
- Feedback integration effectiveness
- Response completeness against user queries

**Efficiency Measures**:
- Generation time per attempt
- Resource utilisation across iterations
- Completion predictability within 3-attempt limit

**Note**: Performance benchmarks and quality thresholds are determined by the Review Agent. The Response Agent interprets pass/fail criteria and incorporates specific feedback for improvement. 