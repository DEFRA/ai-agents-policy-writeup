---
layout: default
title: Review Agent - Prompt Details
parent: Appendix
---

# Review Agent - Complete Prompt Instructions

This appendix provides the complete prompt engineering instructions and technical assessment process used by the Review Agent. For the main technical overview, see [Review Agent](../parliamentary-questions-agents/review-agent.md).

## Core Prompt Mission

The Review Agent operates as a **Parliamentary Question Review Agent** with the specific role of assessing whether responses meet the required standards for Parliamentary Question answers. The prompt positions the agent as a thorough but fair quality assessor responsible for maintaining Parliamentary communication standards.

## Assessment Framework

### 7-Criteria Evaluation System

The prompt establishes a comprehensive evaluation system that the agent must apply systematically:

#### 1. Question Answered
- **Assessment Focus**: Does the response directly address all main aspects of the user's question?
- **Quality Standard**: Key points must be clearly and completely covered
- **Failure Criteria**: Any significant part of the question left unanswered or vague

#### 2. Source Material Accuracy
- **Assessment Focus**: Does the response accurately reflect information in the provided search results?
- **Quality Standard**: Facts, dates, and figures must be correctly cited from source material with most relevant information included
- **Failure Criteria**: Facts misrepresented or key relevant information omitted

#### 3. Information Currency
- **Assessment Focus**: Are specific dates provided where available (not just "recently")?
- **Quality Standard**: Facts and references must be clearly current with proper temporal context
- **Failure Criteria**: Vague temporal references used when specific dates are available

#### 4. Parliamentary Language
- **Assessment Focus**: Is the language formal, professional, and appropriate for ministerial tone?
- **Quality Standard**: Must be completely free from contractions and use formal, professional language
- **Failure Criteria**: Any contractions, colloquialisms, or informal language present

#### 5. Response Length
- **Assessment Focus**: Is the response within acceptable length limit (maximum 200 words)?
- **Quality Standard**: Responses can be shorter than 150 words if they fully answer the question
- **Failure Criteria**: Response exceeds 200 words

#### 6. Contextual Alignment
- **Assessment Focus**: Does the response address the RIGHT TYPE of concern asked about?
- **Quality Standard**: Response must focus on the specific type of impact/concern requested (business/economic vs environmental)
- **Failure Criteria**: Response addresses different type of impact than what was asked

#### 7. Readability and Quality
- **Assessment Focus**: Is the response well-structured with clear flow?
- **Quality Standard**: All sentences must be necessary, add value, and use clear, understandable language
- **Failure Criteria**: Poor structure, redundancy, or genuinely unclear passages

## Evaluation Standards

### Assessment Philosophy: "Be Thorough But Fair"

**Quality Expectations**:
- **Professional Standards**: Responses should meet professional Parliamentary standards
- **Substantive Focus**: Focus on issues that affect quality or accuracy
- **Proportionate Assessment**: Don't fail for trivial imperfections that don't impact the overall message
- **Parliamentary Suitability**: Consider whether a Minister would be comfortable having their name against this statement in the parliamentary record

**Critical Issues Identification**:
The prompt specifically instructs the agent to check for:
1. **Incomplete answers**: Missing significant parts of the question
2. **Factual accuracy**: Information contradicting source material
3. **Informal language**: Any contractions or colloquialisms
4. **Vague dates**: Using "recently" when specific dates are available
5. **Poor source use**: Ignoring highly relevant information from search results
6. **Structural problems**: Confusing flow or redundant information

## Technical Assessment Process

### 1. Question Appropriateness Assessment

**Technical Assessment Process**:
- **Query Analysis**: Systematic comparison of response content against original user query
- **Coverage Evaluation**: Assessment of how completely the response addresses all query aspects
- **Relevance Verification**: Ensuring response content is directly relevant to the question asked
- **Scope Alignment**: Verifying response scope matches query scope and expectations

**Quality Standards**:
- **Direct Addressing**: Response must directly answer the specific question posed
- **Comprehensive Coverage**: All important aspects of the query must be addressed
- **Relevance Maintenance**: All response content must be relevant to the query
- **Scope Appropriateness**: Response detail level must match query specificity

**Feedback Generation**:
- **Missing Elements**: Identification of query aspects not adequately addressed
- **Irrelevant Content**: Highlighting response elements not relevant to the query
- **Scope Misalignment**: Guidance on appropriate response scope and detail level
- **Coverage Gaps**: Specific suggestions for improving query coverage

### 2. Information Currency Assessment

**Technical Assessment Process**:
- **Temporal Analysis**: Evaluation of information recency and current applicability
- **Policy Evolution Tracking**: Understanding of how policies and positions have changed over time
- **Superseded Information Detection**: Identification of outdated or replaced information
- **Current Context Verification**: Ensuring information reflects current governmental positions

**Quality Standards**:
- **Current Accuracy**: All factual information must reflect current status
- **Temporal Relevance**: Information must be applicable to current timeframe
- **Policy Currency**: Policy information must reflect current governmental positions
- **Context Appropriateness**: Historical information included only when relevant to current context

**Feedback Generation**:
- **Outdated Information**: Identification of information that needs updating
- **Missing Current Context**: Suggestions for incorporating recent developments
- **Policy Updates**: Guidance on current policy positions and changes
- **Temporal Context**: Recommendations for appropriate temporal framing

### 3. Parliamentary Language Assessment

**Technical Assessment Process**:
- **Formality Evaluation**: Assessment of appropriate governmental communication tone
- **Terminology Verification**: Checking correct usage of Parliamentary and official terminology
- **Political Neutrality Review**: Ensuring balanced, non-partisan language
- **Professional Standards Compliance**: Verification against governmental communication conventions

**Quality Standards**:
- **Formal Tone**: Appropriate level of formality for governmental communications
- **Correct Terminology**: Accurate use of Parliamentary, legal, and departmental terms
- **Political Neutrality**: Balanced, non-partisan language throughout
- **Professional Courtesy**: Respectful and appropriate language for all stakeholders

**Feedback Generation**:
- **Tone Adjustment**: Guidance on appropriate formality levels
- **Terminology Correction**: Suggestions for correct official terminology usage
- **Neutrality Enhancement**: Recommendations for improving political balance
- **Professional Improvement**: Suggestions for enhancing professional communication standards

### 4. Response Length Assessment

**Technical Assessment Process**:
- **Word Count Analysis**: Systematic counting and evaluation of response length
- **Content Density Evaluation**: Assessment of information density and efficiency
- **Completeness Balance**: Ensuring adequate coverage without excessive verbosity
- **Readability Optimization**: Balancing comprehensiveness with accessibility

**Quality Standards**:
- **Optimal Range**: Target 150-200 words for Parliamentary Question response conventions
- **Content Efficiency**: Maximum information value within word count constraints
- **Completeness Maintenance**: Adequate coverage of all important points
- **Readability Preservation**: Maintaining clarity and accessibility within length limits

**Feedback Generation**:
- **Length Adjustment**: Specific guidance on expanding or condensing content
- **Content Prioritization**: Suggestions for emphasizing most important information
- **Efficiency Improvement**: Recommendations for more efficient information presentation
- **Structure Optimization**: Guidance on organizing content within length constraints

### 5. Contextual Alignment Assessment

**Technical Assessment Process**:
- **Question Type Analysis**: Understanding the specific type of concern or impact being asked about
- **Response Focus Evaluation**: Assessing whether the response addresses the correct domain
- **Stakeholder Perspective Review**: Ensuring appropriate stakeholder focus alignment
- **Impact Category Verification**: Confirming response addresses requested impact type

**Quality Standards**:
- **Type Alignment**: Response must address the specific type of concern requested
- **Focus Consistency**: Maintain consistent focus on the requested domain throughout
- **Stakeholder Appropriateness**: Address correct stakeholder perspectives
- **Impact Relevance**: Focus on requested impact categories (economic, environmental, etc.)

**Feedback Generation**:
- **Focus Correction**: Guidance on shifting response focus to appropriate domain
- **Type Clarification**: Specific instructions on addressing correct concern types
- **Stakeholder Adjustment**: Recommendations for appropriate stakeholder perspective
- **Impact Realignment**: Guidance on addressing requested impact categories

### 6. Readability & Quality Assessment

**Technical Assessment Process**:
- **Clarity Evaluation**: Assessment of clear communication and understanding
- **Structure Analysis**: Evaluation of logical organization and flow
- **Accessibility Review**: Ensuring accessibility for diverse audiences
- **Overall Quality Assessment**: Holistic evaluation of response excellence

**Quality Standards**:
- **Communication Clarity**: Clear, understandable communication throughout
- **Logical Structure**: Well-organized information with logical flow
- **Accessibility**: Appropriate accessibility for target audience
- **Professional Excellence**: High overall quality standards appropriate for governmental communication

**Feedback Generation**:
- **Clarity Enhancement**: Suggestions for improving communication clarity
- **Structure Improvement**: Recommendations for better organization and flow
- **Accessibility Optimization**: Guidance on improving accessibility
- **Quality Enhancement**: General recommendations for overall quality improvement

## Required Output Format

The prompt mandates a specific, structured output format:

### Assessment Structure
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

### Feedback Generation Requirements

**Feedback Conditions**: 
- **When Required**: If the response failed assessment
- **Content Requirements**: SPECIFIC, ACTIONABLE feedback for each failed criterion

**Feedback Structure**: For each failed criterion, explain:
1. **Problem Identification**: What exactly was wrong (quote specific problematic phrases if helpful)
2. **Solution Guidance**: How to fix it (provide concrete suggestions)
3. **Source Integration**: What specific information from source material should be used

**Feedback Examples**:
- **Temporal Issues**: "Replace 'recently' in paragraph 2 with the specific date '2024' from the source material"
- **Language Issues**: "The response uses 'we've' - change to 'we have' to remove the contraction"
- **Content Issues**: "Add information about the glass sector consultation mentioned in source PQ 1234567"
- **Structure Issues**: "Second paragraph is redundant - combine with first paragraph to reduce word count"

**Feedback Style**: 
- **Direct and Specific**: Clear instructions for improvement
- **Action-Oriented**: Concrete guidance for the response agent
- **Source-Referenced**: Specific references to available source material

## Pass/Fail Decision Logic

The prompt establishes clear binary decision-making:

**Pass Criteria**: Response meets ALL 7 criteria to Parliamentary standards
**Fail Criteria**: One or more criteria require improvement before acceptance
**Decision Clarity**: Clear documentation of assessment outcomes with specific reasoning

## Assessment Context Integration

The prompt requires the agent to consider multiple information sources:

**Input Context**:
1. **Original User Question**: Complete understanding of what was asked
2. **Available Source Material**: Filtered search results for accuracy verification
3. **Response to Review**: The actual response requiring assessment

**Contextual Assessment**: The agent must evaluate responses within the full context of available information and user requirements.

## Quality Assurance Methodology

### Systematic Evaluation Process

**Individual Criterion Review**: Each criterion is evaluated independently with detailed analysis
**Comprehensive Assessment**: All criteria are considered together for overall quality determination
**Evidence-Based Evaluation**: Assessment based on specific evidence from response content
**Consistent Standards**: Uniform application of criteria across all responses

### Assessment Accuracy Standards

**Criterion Evaluation Precision**: Accuracy of individual criterion assessment against Parliamentary standards
**Overall Quality Determination**: Reliability of pass/fail decisions for workflow routing
**Feedback Relevance**: Quality and usefulness of generated improvement suggestions
**Standards Consistency**: Uniform application of Parliamentary standards across all assessments

### Edge Case Handling

**Marginal Quality Responses**:
**Scenario**: Responses that partially meet criteria but have borderline quality
**Handling**: Conservative assessment with detailed feedback for improvement areas
**Rationale**: Maintain standards while providing guidance for enhancement

**Ambiguous Criterion Application**:
**Scenario**: Situations where criterion application is unclear or subjective
**Handling**: Detailed analysis with explicit reasoning for assessment decision
**Rationale**: Maintain consistency while providing transparency about decision basis

**Novel Content Types**:
**Scenario**: Responses addressing topics or formats not previously encountered
**Handling**: Apply core Parliamentary principles with adaptive assessment
**Rationale**: Maintain quality standards while accommodating legitimate innovation 