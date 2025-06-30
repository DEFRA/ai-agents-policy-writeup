---
layout: default
title: Review Agent
parent: Parliamentary Questions Agentic Workflow
---

# Review Agent

## Overview

The Review Agent serves as the quality assurance checkpoint in the Parliamentary Questions workflow. It evaluates response quality against Parliamentary standards and implements conditional routing for iterative improvement.

**Core Function**: Automated assessment of Parliamentary Question responses using a 7-criteria framework with pass/fail determination and specific feedback generation.

**Key Capabilities**:
- Systematic evaluation against Parliamentary communication standards
- Conditional routing with feedback loops (max 3 attempts)
- Detailed improvement guidance for failed assessments
- Loop prevention to ensure workflow completion

## Design Decisions

### Why Automated Review?
- **Consistency**: Eliminates human reviewer variability and subjective bias
- **Scalability**: Enables quality assessment at scale without resource constraints
- **Standards Compliance**: Ensures systematic application of Parliamentary communication requirements
- **Objectivity**: Maintains focus on measurable quality criteria

### Why 7-Criteria Framework?
The framework covers all critical Parliamentary communication dimensions:
1. **Question Answered** - Content completeness
2. **Source Material Accuracy** - Factual verification
3. **Information Currency** - Temporal relevance
4. **Parliamentary Language** - Formal tone and professional language
5. **Response Length** - 200-word maximum compliance
6. **Contextual Alignment** - Appropriate response focus
7. **Readability and Quality** - Structure and clarity

### Why Conditional Routing with Feedback Loops?
- **Quality Optimization**: Enables systematic improvement through specific feedback
- **Resource Management**: 3-attempt limit prevents infinite loops
- **Efficiency Balance**: Optimizes quality while maintaining operational requirements
- **Deterministic Completion**: Guarantees workflow completion within predictable timeframes

## Implementation Details

### Assessment Process

**Input Requirements**:
- Original user question
- Available source material (filtered search results)  
- Response to review

**Evaluation Workflow**:
1. **Individual Criterion Assessment**: Each criterion evaluated independently
2. **Binary Decision**: Pass (all criteria met) or Fail (one or more criteria require improvement)
3. **Feedback Generation**: Specific, actionable guidance for failed criteria
4. **Routing Decision**: If **Pass**: JSON Formatter Else **Fail**: Response Agent (with attempt tracking)

### Assessment Criteria Details

#### 1. Question Answered
- **Standard**: Response directly addresses all main aspects of user's question
- **Failure**: Significant parts unanswered or vague
- **Example Feedback**: "Add information about the glass sector consultation mentioned in source PQ 1234567"

#### 2. Source Material Accuracy  
- **Standard**: Facts, dates, figures correctly cited from source material
- **Failure**: Facts misrepresented or key relevant information omitted
- **Example Feedback**: "The response states 2023 but source shows 2024 - correct the date"

#### 3. Information Currency
- **Standard**: Specific dates provided where available (not vague terms like "recently")
- **Failure**: Vague temporal references when specific dates available
- **Example Feedback**: "Replace 'recently' in paragraph 2 with specific date '2024' from source material"

#### 4. Parliamentary Language
- **Standard**: Formal, professional tone with no contractions
- **Failure**: Any contractions, colloquialisms, or informal language
- **Example Feedback**: "Change 'we've' to 'we have' to remove contraction"

#### 5. Response Length
- **Standard**: Maximum 200 words (can be shorter if complete)
- **Failure**: Exceeds 200 words
- **Example Feedback**: "Second paragraph is redundant - combine with first paragraph to reduce word count"

#### 6. Contextual Alignment
- **Standard**: Response addresses the correct type of concern requested
- **Failure**: Response addresses different impact type than asked (e.g., environmental vs economic)
- **Example Feedback**: "Question asks about economic impacts but response focuses on environmental - refocus content"

#### 7. Readability and Quality
- **Standard**: Well-structured with clear flow, all sentences necessary and valuable
- **Failure**: Poor structure, redundancy, unclear passages
- **Example Feedback**: "Reorganize paragraphs for logical flow and remove redundant sentences"

### Conditional Routing Logic

```
Assessment Result → Routing Decision:
├── PASS → Continue to JSON Formatter
├── FAIL + Attempts < 3 → Return to Response Agent with feedback
└── FAIL + Attempts = 3 → Continue to JSON Formatter (prevent infinite loops)
```

**Loop Prevention Strategy**:
- Hard limit: 3 improvement cycles maximum
- Progress tracking across iterations  
- Completion prioritized over perfect quality after max attempts
- Resource management and operational efficiency

## Prompt Engineering

### Core Prompt Structure

**Agent Role**: Parliamentary Question Review Agent responsible for maintaining Parliamentary communication standards

**Assessment Philosophy**: "Be Thorough But Fair"
- Focus on substantive quality issues
- Don't fail for trivial imperfections
- Consider whether a Minister would be comfortable having their name against this statement in the parliamentary record

**Required Output Format**:
```
**REVIEW ASSESSMENT:**
1. Question Answered: [YES/NO]
2. Source Material Accuracy: [YES/NO]  
3. Information Currency: [YES/NO]
4. Parliamentary Language: [YES/NO]
5. Response Length (max 200 words): [YES/NO] - [ACTUAL WORD COUNT]
6. Contextual Alignment: [YES/NO]
7. Readability and Quality: [YES/NO]

**OVERALL RESULT: [PASS/FAIL]**
```

**Feedback Requirements** (if FAIL):
- Specific problem identification with quotes where helpful
- Concrete solution guidance
- Source material integration suggestions
- Direct, action-oriented language

*See [Review Agent - Prompt Details](../appendix/review-agent-prompt-details.md) for complete implementation details.*

## Error Handling

### Edge Cases
- **Marginal Quality**: Conservative assessment with detailed feedback
- **Ambiguous Criteria**: Detailed analysis with explicit reasoning
- **Novel Content**: Apply core Parliamentary principles adaptively

### System Failures
- **Processing Errors**: Default to quality-focused handling with manual review flags
- **Feedback Generation Failures**: Provide general guidance while flagging for manual review

## Technical Considerations

### Performance Characteristics
- **Assessment Speed**: Single-pass evaluation across all criteria
- **Feedback Quality**: Specific, actionable improvement suggestions
- **Resource Usage**: Optimized for efficiency within quality constraints
- **Consistency**: Uniform standards application across all assessments

### Integration Points
- **Input**: User question, source material, response text
- **Output**: Pass/fail decision, detailed feedback, routing instructions
- **State Management**: Attempt tracking, feedback history, quality metrics 