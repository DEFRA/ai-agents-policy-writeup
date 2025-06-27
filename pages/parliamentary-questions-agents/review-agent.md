---
layout: default
title: Review Agent
parent: Parliamentary Questions Agentic Workflow
---

# Review Agent

## Overview
The Review Agent functions as the critical quality assurance checkpoint in our Parliamentary Questions workflow, implementing sophisticated automated assessment against Parliamentary communication standards while providing detailed feedback for systematic response improvement through conditional routing and iterative enhancement mechanisms.

## Prompt Instructions & Agent Behavior

### Core Prompt Mission
The Review Agent operates as a **Parliamentary Question Review Agent** with the specific role of assessing whether responses meet the required standards for Parliamentary Question answers. The prompt positions the agent as a thorough but fair quality assessor responsible for maintaining Parliamentary communication standards.

### Assessment Framework
The prompt establishes a comprehensive **7-criteria evaluation system** that the agent must apply systematically:

**1. Question Answered**:
- **Assessment Focus**: Does the response directly address all main aspects of the user's question?
- **Quality Standard**: Key points must be clearly and completely covered
- **Failure Criteria**: Any significant part of the question left unanswered or vague

**2. Source Material Accuracy**:
- **Assessment Focus**: Does the response accurately reflect information in the provided search results?
- **Quality Standard**: Facts, dates, and figures must be correctly cited from source material with most relevant information included
- **Failure Criteria**: Facts misrepresented or key relevant information omitted

**3. Information Currency**:
- **Assessment Focus**: Are specific dates provided where available (not just "recently")?
- **Quality Standard**: Facts and references must be clearly current with proper temporal context
- **Failure Criteria**: Vague temporal references used when specific dates are available

**4. Parliamentary Language**:
- **Assessment Focus**: Is the language formal, professional, and appropriate for ministerial tone?
- **Quality Standard**: Must be completely free from contractions and use British English spelling consistently
- **Failure Criteria**: Any contractions, colloquialisms, informal language, or American spelling present

**5. Response Length**:
- **Assessment Focus**: Is the response within acceptable length limit (maximum 200 words)?
- **Quality Standard**: Responses can be shorter than 150 words if they fully answer the question
- **Failure Criteria**: Response exceeds 200 words

**6. Contextual Alignment**:
- **Assessment Focus**: Does the response address the RIGHT TYPE of concern asked about?
- **Quality Standard**: Response must focus on the specific type of impact/concern requested (business/economic vs environmental)
- **Failure Criteria**: Response addresses different type of impact than what was asked

**7. Readability and Quality**:
- **Assessment Focus**: Is the response well-structured with clear flow?
- **Quality Standard**: All sentences must be necessary, add value, and use clear, understandable language
- **Failure Criteria**: Poor structure, redundancy, or genuinely unclear passages

### Evaluation Standards
The prompt establishes **"Be Thorough But Fair"** as the core evaluation philosophy:

**Quality Expectations**:
- **Professional Standards**: Responses should meet professional Parliamentary standards
- **Substantive Focus**: Focus on issues that affect quality or accuracy
- **Proportionate Assessment**: Don't fail for trivial imperfections that don't impact the overall message
- **Ministerial Test**: Consider whether a Minister would be comfortable delivering this response

**Critical Issues Identification**:
The prompt specifically instructs the agent to check for:
1. **Incomplete answers**: Missing significant parts of the question
2. **Factual accuracy**: Information contradicting source material
3. **Informal language**: Any contractions or colloquialisms
4. **Vague dates**: Using "recently" when specific dates are available
5. **Poor source use**: Ignoring highly relevant information from search results
6. **Structural problems**: Confusing flow or redundant information

### Required Output Format
The prompt mandates a specific, structured output format:

**Assessment Structure**:
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
The prompt provides detailed guidance for feedback generation:

**Feedback Conditions**: 
- **When Required**: If the response failed assessment
- **Content Requirements**: SPECIFIC, ACTIONABLE feedback for each failed criterion

**Feedback Structure**: For each failed criterion, explain:
1. **Problem Identification**: What exactly was wrong (quote specific problematic phrases if helpful)
2. **Solution Guidance**: How to fix it (provide concrete suggestions)
3. **Source Integration**: What specific information from source material should be used

**Feedback Examples**: The prompt provides specific examples:
- **Temporal Issues**: "Replace 'recently' in paragraph 2 with the specific date '2024' from the source material"
- **Language Issues**: "The response uses 'we've' - change to 'we have' to remove the contraction"
- **Content Issues**: "Add information about the glass sector consultation mentioned in source PQ 1234567"
- **Structure Issues**: "Second paragraph is redundant - combine with first paragraph to reduce word count"

**Feedback Style**: 
- **Direct and Specific**: Clear instructions for improvement
- **Action-Oriented**: Concrete guidance for the response agent
- **Source-Referenced**: Specific references to available source material

### British English Compliance
The prompt mandates **British English spelling and grammar conventions** for both feedback and assessment, ensuring consistency with Parliamentary standards. This includes specific assessment of British English compliance in responses (realise, organise, colour, favour, centre, analyse, whilst, amongst).

### Pass/Fail Decision Logic
The prompt establishes clear binary decision-making:

**Pass Criteria**: Response meets ALL 7 criteria to Parliamentary standards
**Fail Criteria**: One or more criteria require improvement before acceptance
**Decision Clarity**: Clear documentation of assessment outcomes with specific reasoning

### Assessment Context Integration
The prompt requires the agent to consider multiple information sources:

**Input Context**:
1. **Original User Question**: Complete understanding of what was asked
2. **Available Source Material**: Filtered search results for accuracy verification
3. **Response to Review**: The actual response requiring assessment

**Contextual Assessment**: The agent must evaluate responses within the full context of available information and user requirements.

## Technical Design Philosophy

### Why Automated Parliamentary Review?

**Consistency and Objectivity**:
- **Standardized Assessment**: Eliminates human reviewer variability and subjective bias in quality evaluation
- **Reproducible Criteria**: Ensures consistent application of Parliamentary standards across all responses
- **Objective Evaluation**: Removes personal preferences and maintains focus on professional standards
- **Scalable Quality Assurance**: Enables consistent quality assessment at scale without human resource constraints

**Domain-Specific Expertise**:
- **Parliamentary Context Understanding**: Specialized knowledge of governmental communication requirements
- **Professional Standards Integration**: Deep understanding of formal governmental language conventions
- **Political Sensitivity Awareness**: Recognition of appropriate handling of sensitive political topics
- **Compliance Framework**: Comprehensive understanding of Parliamentary Question response standards

### Why Six-Criteria Assessment Framework?

**Comprehensive Coverage Strategy**:
Our six-criteria framework was designed to address all critical aspects of Parliamentary communication quality:
1. **Content Appropriateness**: Ensures responses directly address user queries
2. **Information Currency**: Validates temporal relevance and accuracy
3. **Language Standards**: Enforces Parliamentary communication conventions
4. **Format Compliance**: Maintains optimal response length and structure
5. **Sensitivity Management**: Ensures appropriate handling of political topics
6. **Quality Assurance**: Validates readability and overall excellence

**Assessment Balance**:
- **Objective Criteria**: Measurable standards that can be consistently applied
- **Subjective Elements**: Nuanced assessment requiring sophisticated reasoning
- **Comprehensive Scope**: Coverage of all major quality dimensions
- **Actionable Feedback**: Criteria designed to generate specific improvement guidance

### Why Conditional Routing with Feedback Loops?

**Quality vs. Efficiency Optimization**:
- **Iterative Improvement**: Allows systematic enhancement of failed responses
- **Resource Management**: Prevents infinite loops while enabling meaningful improvement
- **Quality Gates**: Ensures minimum standards while maintaining operational efficiency
- **Deterministic Completion**: Guarantees workflow completion within predictable timeframes

**Learning Integration**:
- **Feedback-Driven Enhancement**: Enables targeted improvement based on specific quality shortcomings
- **Progressive Quality**: Each iteration should improve upon previous attempts
- **Standards Alignment**: Systematic progression toward Parliamentary compliance
- **Process Transparency**: Clear visibility into quality assessment and improvement processes

## Primary Function
Assesses responses against 6 Parliamentary criteria including appropriateness, currency, language, length, sensitivity, and readability. Provides pass/fail determination with specific improvement feedback while implementing conditional routing to enable iterative response enhancement.

## Technical Implementation

### Assessment Architecture

**Multi-Criteria Evaluation System**:
The Review Agent employs a sophisticated assessment framework that evaluates responses across six distinct but interconnected quality dimensions:

**Systematic Assessment Process**:
1. **Individual Criterion Evaluation**: Each criterion is assessed independently with specific focus
2. **Cross-Criterion Analysis**: Understanding interactions and dependencies between different quality aspects
3. **Holistic Assessment**: Overall quality determination based on comprehensive criterion evaluation
4. **Feedback Generation**: Specific improvement guidance for failed criteria

**LLM-Powered Assessment**:
- **Contextual Understanding**: Sophisticated reasoning about Parliamentary communication requirements
- **Nuanced Evaluation**: Understanding of subtle quality issues beyond simple rule-based checking
- **Adaptive Assessment**: Ability to handle novel situations and edge cases appropriately
- **Detailed Feedback**: Generation of specific, actionable improvement suggestions

### Conditional Routing Implementation

**Dynamic Workflow Control**:
**Technical Implementation**: Intelligent routing based on assessment outcomes and attempt tracking
**Decision Logic**: 
- Pass → Continue to JSON Formatter
- Fail + Attempts < 3 → Return to Response Agent with feedback
- Fail + Max Attempts → Continue to JSON Formatter (prevent infinite loops)

**Loop Prevention Strategy**:
- **Attempt Limiting**: Maximum 3 improvement cycles balances quality with efficiency
- **Progress Tracking**: Monitoring improvement across iterations
- **Quality vs. Completion**: Prioritizes workflow completion over perfect quality after maximum attempts
- **Resource Management**: Prevents excessive computational resource usage

## Parliamentary Assessment Criteria

### 1. Question Appropriateness Assessment

**Evaluation Focus**: Does the response directly address the user's query?

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

**Evaluation Focus**: Are facts up-to-date and relevant?

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

**Evaluation Focus**: Is the tone and terminology appropriate for Parliamentary context?

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

**Evaluation Focus**: Is the response within the optimal 150-200 word range?

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

### 5. Sensitive Topics Assessment

**Evaluation Focus**: Are sensitive political topics handled appropriately?

**Technical Assessment Process**:
- **Sensitivity Detection**: Identification of politically sensitive topics and content
- **Balance Evaluation**: Assessment of fair treatment of different perspectives
- **Diplomatic Language Review**: Ensuring appropriate diplomatic and respectful language
- **Controversy Management**: Evaluation of appropriate handling of controversial issues

**Quality Standards**:
- **Political Sensitivity**: Appropriate recognition and handling of political sensitivities
- **Balanced Treatment**: Fair representation of different perspectives when appropriate
- **Diplomatic Language**: Use of respectful, diplomatic language for sensitive topics
- **Controversy Avoidance**: Avoiding unnecessary controversy while addressing issues honestly

**Feedback Generation**:
- **Sensitivity Guidance**: Recommendations for handling sensitive topics appropriately
- **Balance Improvement**: Suggestions for improving perspective balance
- **Language Refinement**: Guidance on more diplomatic language choices
- **Controversy Mitigation**: Strategies for addressing issues without unnecessary controversy

### 6. Readability & Quality Assessment

**Evaluation Focus**: Is the response clear, well-structured, and accessible?

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

## Quality Assurance Process

### Assessment Methodology

**Systematic Evaluation**:
- **Individual Criterion Review**: Each criterion is evaluated independently with detailed analysis
- **Comprehensive Assessment**: All criteria are considered together for overall quality determination
- **Evidence-Based Evaluation**: Assessment based on specific evidence from response content
- **Consistent Standards**: Uniform application of criteria across all responses

**Pass/Fail Determination**:
- **Binary Decision**: Clear pass or fail determination for workflow routing
- **Evidence-Based**: Decision supported by specific evidence and analysis
- **Comprehensive Evaluation**: Based on performance across all six criteria
- **Transparency**: Clear reasoning provided for all assessment decisions

### Feedback Generation System

**Specific Issue Identification**:
- **Criterion-Based Feedback**: Specific feedback for each failed criterion
- **Evidence-Supported**: Feedback based on specific evidence from response analysis
- **Actionable Guidance**: Concrete suggestions for improvement
- **Priority Indication**: Guidance on most critical improvements needed

**Improvement Strategy Development**:
- **Targeted Enhancement**: Focused improvement suggestions rather than general revision
- **Systematic Approach**: Structured approach to addressing quality issues
- **Progressive Improvement**: Building upon successful elements while addressing weaknesses
- **Standards Alignment**: Guidance toward Parliamentary standards compliance

### Loop Prevention and Management

**Attempt Limiting Strategy**:
- **Maximum Attempts**: Hard limit of 3 improvement cycles
- **Progress Monitoring**: Tracking improvement across iterations
- **Quality vs. Efficiency**: Balancing quality optimization with operational requirements
- **Completion Assurance**: Ensuring workflow completion even with imperfect quality

**Quality Optimization**:
- **Iterative Enhancement**: Systematic improvement through feedback integration
- **Learning Integration**: Building upon insights from previous attempts
- **Standards Convergence**: Progressive alignment with Parliamentary standards
- **Efficiency Balance**: Optimizing quality improvement within resource constraints

## Error Handling and Edge Cases

### Assessment Edge Cases

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

### System Integration Failures

**Review Processing Errors**:
**Scenario**: Technical failures during assessment processing
**Handling**: Default to quality-focused error handling with manual review flags
**Rationale**: Prioritize quality maintenance while ensuring system reliability

**Feedback Generation Failures**:
**Scenario**: Inability to generate specific improvement feedback
**Handling**: Provide general improvement guidance while flagging for manual review
**Rationale**: Maintain workflow completion while preserving improvement opportunities

## Performance Characteristics

### Assessment Accuracy

**Criterion Evaluation Precision**: Accuracy of individual criterion assessment against Parliamentary standards
**Overall Quality Determination**: Reliability of pass/fail decisions for workflow routing
**Feedback Relevance**: Quality and usefulness of generated improvement suggestions
**Standards Consistency**: Uniform application of Parliamentary standards across all assessments

### System Efficiency

**Assessment Speed**: Time required for comprehensive quality evaluation
**Feedback Generation Efficiency**: Speed and quality of improvement suggestion generation
**Routing Decision Speed**: Efficiency of conditional routing decision-making
**Resource Utilization**: Computational resource usage for quality assessment processes

The Review Agent represents the critical quality assurance capability of our Parliamentary Questions analysis system, implementing sophisticated automated assessment of Parliamentary communication standards while providing systematic improvement mechanisms through conditional routing and feedback integration. Its design ensures consistent quality standards application while maintaining operational efficiency and predictable workflow completion. 