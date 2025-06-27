---
layout: default
title: Response Agent
parent: Parliamentary Questions Agentic Workflow
---

# Response Agent

## Overview
The Response Agent serves as the primary content generation engine, transforming structured Parliamentary information into formal, Parliamentary-standard responses that meet governmental communication requirements while incorporating sophisticated iterative improvement mechanisms based on quality assessment feedback.

## Prompt Instructions & Agent Behavior

### Core Prompt Mission
The Response Agent is positioned as a **specialist policy writer in Defra's Circular Economy Policy team** with expertise in composing comprehensive Parliamentary Question responses. The prompt establishes the agent as a professional governmental communicator responsible for creating formal, authoritative responses that meet Parliamentary standards.

### Specific Task Instructions
The prompt provides a detailed composition framework:

**Input Processing Requirements**:
1. **New Question Review**: Systematic analysis of the Parliamentary Question requiring response
2. **Key Elements Integration**: Utilization of pre-extracted and categorized information from relevant past Parliamentary Questions

**Response Composition Process**:
The prompt outlines a 4-step systematic approach:

**Step 1 - Review and Analysis**:
- **Priority Identification**: Focus on elements marked as "Direct Answer - High" relevance
- **Context Assessment**: Evaluate supporting context and evidence available
- **Timeline Integration**: Note sequencing of government actions for chronological accuracy

**Step 2 - Response Structure**:
The prompt mandates a specific three-part structure:
- **Opening**: Clear statement of government position (1 sentence)
- **Body**: Multiple paragraphs incorporating relevant facts and evidence
- **Closing**: Policy action or next steps, if applicable

**Step 3 - Synthesis Guidelines**:
The prompt provides detailed composition requirements:
- **Primary Focus**: Start with the most direct answer to the question
- **Formal Language**: Use formal Parliamentary language throughout
- **Contraction Prohibition**: Explicit ban on contractions (use "cannot" not "can't", "will not" not "won't")
- **Detail Integration**: Include specific dates, figures, and study references where available
- **Narrative Construction**: Build demonstrating thorough government consideration
- **Value Addition**: Ensure every sentence adds value and supports the answer
- **Length Optimization**: Aim for 200-300 words for comprehensive coverage, shorter if fully addressing question
- **Citation Exclusion**: DO NOT include source references, citations, or PQ numbers in final response

**Step 4 - Language Requirements**:
The prompt establishes strict linguistic standards:
- **British English Compliance**: British spelling, grammar, and vocabulary conventions throughout
- **Voice and Perspective**: Use passive voice where appropriate, avoid first person pronouns, use "The Government" rather than "We"
- **Tone Management**: Maintain neutral, professional tone
- **Speculation Avoidance**: Avoid speculative language
- **Specific Information**: Include dates, figures, and study references where available

### Quality Control Framework
The prompt includes a 4-point quality verification system:

**Quality Checks**:
1. **Direct Addressing**: Does the response directly answer the question asked?
2. **Evidence Support**: Are all facts supported by the provided key elements?
3. **Language Appropriateness**: Is the language appropriate for Parliament?
4. **Completeness Assessment**: Would this leave the MP with no obvious follow-up questions?

### Response Format Requirements
The prompt specifies exact output formatting:

**Required Output Structure**:
- **Opening Statement**: One-sentence summary of government position
- **Multi-paragraph Body**: Comprehensive response incorporating relevant information with specific facts, figures, and policy details
- **Closing Statement**: Policy action or next step, if any

### Synthesis and Writing Guidelines
The prompt provides specific writing techniques:

**Advanced Synthesis**:
- **Information Consolidation**: Synthesize multiple key elements addressing the same point into stronger statements
- **Transition Management**: Use phrases to connect different aspects smoothly
- **Data Integration**: Integrate dates and figures naturally into sentences
- **Active Government Positioning**: Prefer active government actions ("The Government has..." rather than "It is...")
- **Logical Flow**: Ensure response flows from general position to specific details

### Prohibited Practices
The prompt explicitly forbids:

**Content Restrictions**:
- **Information Addition**: Introducing information not present in key elements
- **Rhetorical Questions**: Asking questions in responses
- **Unauthorized Commitments**: Making commitments beyond source material
- **Informal Language**: Using conversational or casual language
- **Uncertainty Creation**: Creating doubt where key elements show clarity
- **Speculation**: Future actions not mentioned in sources
- **Source References**: Including citations, PQ numbers, or source references

### British English Compliance
The prompt mandates **British English spelling and grammar conventions**, ensuring consistency with Parliamentary standards and maintaining appropriate governmental language use throughout response generation.

### Professional Standards Integration
The prompt emphasizes **Parliamentary communication standards**:
- **Formal Register**: Appropriate level of formality for governmental communication
- **Professional Authority**: Responses must reflect governmental authority appropriately
- **Neutral Positioning**: Maintain non-partisan, professional governmental stance
- **Comprehensive Coverage**: Address all aspects of user queries systematically

## Technical Design Philosophy

### Why Dedicated Response Generation?

**Specialized Content Creation**:
- **Focus Optimization**: Dedicated response generation allows specialized optimization for Parliamentary language, tone, and content standards
- **Quality Consistency**: Consistent application of formal governmental communication standards across all responses
- **Iterative Improvement**: Enables systematic response enhancement through feedback integration
- **Template Adherence**: Maintains adherence to Parliamentary Question response conventions and formatting

**Separation from Assessment**:
- **Cognitive Separation**: Isolates creative content generation from critical quality assessment
- **Bias Reduction**: Prevents assessment criteria from constraining creative response generation
- **Process Clarity**: Clear distinction between generation and evaluation phases
- **Optimization Independence**: Allows independent optimization of generation vs. assessment processes

### Why Iterative Improvement Architecture?

**Quality Optimization Strategy**:
- **Progressive Enhancement**: Each iteration builds upon previous attempts with specific improvement guidance
- **Learning Integration**: Systematic incorporation of feedback to address identified shortcomings
- **Standards Alignment**: Iterative approach ensures responses progressively align with Parliamentary standards
- **Failure Recovery**: Provides mechanism to recover from initial response quality issues

**Efficiency Balance**:
- **Bounded Iteration**: Maximum 3 attempts prevents excessive processing while allowing meaningful improvement
- **Targeted Improvement**: Feedback-driven enhancement focuses on specific quality issues rather than general revision
- **Resource Management**: Balances quality optimization with computational and time efficiency
- **Predictable Completion**: Ensures workflow completion within reasonable timeframes

## Primary Function
Generates Parliamentary-standard responses (150-200 words) using formal language and tone. Incorporates review feedback for iterative improvement across multiple attempts, maintaining appropriate governmental communication standards while ensuring comprehensive coverage of user queries.

## Technical Implementation

### Parliamentary Standards Integration

**Language and Tone Management**:
- **Formal Register**: Maintains appropriate level of formality for governmental communications
- **Political Neutrality**: Ensures balanced, non-partisan language that respects political sensitivities
- **Respectful Terminology**: Uses appropriate titles, references, and diplomatic language conventions
- **Technical Accuracy**: Ensures correct use of Parliamentary, legal, and departmental terminology

**Content Structure Optimization**:
- **Logical Organization**: Clear introduction, substantive body, and appropriate conclusion
- **Comprehensive Coverage**: Addresses all aspects of user queries based on structured key elements
- **Evidence Integration**: Seamlessly incorporates factual information and official sources
- **Word Count Management**: Optimizes content for 150-200 word target while maintaining completeness

### History-Aware Generation Architecture

**Context Preservation**:
**Technical Implementation**: Maintains complete awareness of previous response attempts and their specific shortcomings
**Benefits**: Enables progressive improvement that builds upon successful elements while addressing identified weaknesses

**Feedback Integration Mechanism**:
**Technical Implementation**: Systematic incorporation of Review Agent feedback into subsequent generation attempts
**Benefits**: Targeted improvement that addresses specific quality issues rather than general revision

**Iterative Enhancement Strategy**:
**Technical Implementation**: Each attempt leverages cumulative learning from all previous attempts and feedback
**Benefits**: Progressive quality improvement with specific attention to Parliamentary standards compliance

**Attempt Tracking System**:
**Technical Implementation**: Comprehensive tracking of response evolution with metadata about changes and improvements
**Benefits**: Complete audit trail of response development for debugging and quality analysis

### Advanced Content Generation

**Structured Information Synthesis**:
- **Key Elements Integration**: Systematic incorporation of extracted themes, stakeholders, policies, and facts
- **Relationship Preservation**: Maintains important connections between different information elements
- **Context Weaving**: Seamlessly integrates diverse information sources into coherent narrative
- **Priority Emphasis**: Focuses attention on most important aspects identified during extraction

**Parliamentary Context Adaptation**:
- **Audience Awareness**: Tailors content for Parliamentary Question response conventions
- **Authority Positioning**: Ensures responses reflect appropriate governmental authority and responsibility
- **Compliance Integration**: Incorporates relevant regulatory and policy compliance considerations
- **Stakeholder Sensitivity**: Appropriately acknowledges different stakeholder perspectives and interests

## Response Standards

### Parliamentary Language Compliance

**Formal Tone Requirements**:
**Technical Implementation**: Systematic application of formal governmental communication standards
**Quality Assurance**: Regular assessment against Parliamentary language conventions
**Benefits**: Ensures responses meet professional governmental communication standards

**Political Neutrality Enforcement**:
**Technical Implementation**: Careful balance of perspectives and avoidance of partisan language
**Quality Assurance**: Review for political bias and inappropriate advocacy
**Benefits**: Maintains governmental neutrality and professional objectivity

**Respectful Terminology Standards**:
**Technical Implementation**: Appropriate use of titles, formal references, and diplomatic language
**Quality Assurance**: Verification of correct terminology and respectful address
**Benefits**: Ensures responses meet governmental courtesy and respect standards

**Technical Accuracy Requirements**:
**Technical Implementation**: Correct usage of Parliamentary, legal, and departmental terminology
**Quality Assurance**: Verification against official terminology and usage guidelines
**Benefits**: Maintains professional accuracy and governmental credibility

### Content Requirements

**Comprehensive Coverage Standards**:
**Technical Implementation**: Systematic address of all aspects identified in user queries and key elements
**Quality Assurance**: Verification that responses address all important query components
**Benefits**: Ensures complete and satisfactory responses to user inquiries

**Factual Accuracy Requirements**:
**Technical Implementation**: Careful integration of verified factual information from Parliamentary sources
**Quality Assurance**: Cross-reference checking against authoritative sources
**Benefits**: Maintains governmental credibility and accuracy standards

**Appropriate Sourcing Standards**:
**Technical Implementation**: Reference to authoritative Parliamentary and governmental sources
**Quality Assurance**: Verification of source authority and appropriateness
**Benefits**: Ensures responses are grounded in official and credible information

**Currency Requirements**:
**Technical Implementation**: Focus on current and relevant information with appropriate temporal context
**Quality Assurance**: Assessment of information relevance and up-to-date accuracy
**Benefits**: Ensures responses reflect current governmental positions and situations

### Format Specifications

**Word Count Optimization**:
**Technical Implementation**: Systematic optimization for 150-200 word target range
**Quality Assurance**: Automated word count tracking with optimization guidance
**Benefits**: Ensures responses meet Parliamentary Question response length conventions

**Structural Clarity Requirements**:
**Technical Implementation**: Clear introduction, substantive body, and appropriate conclusion structure
**Quality Assurance**: Assessment of logical flow and structural coherence
**Benefits**: Ensures responses are well-organized and easily understood

**Accessibility Standards**:
**Technical Implementation**: Plain English principles while maintaining formal tone
**Quality Assurance**: Readability assessment and accessibility verification
**Benefits**: Ensures responses are accessible to diverse audiences while maintaining professionalism

**Coherence Requirements**:
**Technical Implementation**: Logical flow and clear connections between ideas and information
**Quality Assurance**: Assessment of logical organization and idea connectivity
**Benefits**: Ensures responses are coherent and easy to follow

## Iterative Improvement Process

### Multi-Attempt Architecture

**First Attempt Generation**:
- **Foundation Building**: Initial response based on structured key elements and user query
- **Standards Application**: Application of Parliamentary language and content standards
- **Comprehensive Coverage**: Attempt to address all aspects of the user query
- **Quality Baseline**: Establishment of initial quality baseline for subsequent improvement

**Feedback-Driven Enhancement**:
- **Specific Issue Targeting**: Each subsequent attempt focuses on specific issues identified in feedback
- **Progressive Improvement**: Building upon successful elements while addressing weaknesses
- **Standards Alignment**: Continuous alignment with Parliamentary standards through feedback integration
- **Quality Convergence**: Systematic approach to achieving quality standards compliance

**Attempt Limitation Strategy**:
- **Resource Management**: Maximum 3 attempts balances quality optimization with efficiency
- **Completion Assurance**: Ensures workflow completion even if perfect quality isn't achieved
- **Quality vs. Efficiency**: Balances quality improvement with operational requirements
- **Predictable Processing**: Ensures predictable response times for API consumers

### Feedback Integration Methodology

**Review Analysis**:
- **Issue Identification**: Systematic analysis of Review Agent feedback to identify specific shortcomings
- **Priority Assessment**: Understanding which feedback elements are most critical for improvement
- **Strategy Development**: Developing specific improvement strategies for identified issues
- **Implementation Planning**: Planning specific changes to address feedback comprehensively

**Targeted Improvement**:
- **Specific Enhancement**: Making targeted improvements rather than general revision
- **Feedback Compliance**: Ensuring improvements directly address identified issues
- **Quality Preservation**: Maintaining successful elements while improving problematic areas
- **Progressive Enhancement**: Building systematically toward Parliamentary standards compliance

## Quality Assurance Integration

### Response Assessment Preparation

**Self-Assessment Integration**:
- **Standards Awareness**: Built-in awareness of Parliamentary assessment criteria
- **Quality Prediction**: Anticipating potential quality issues before formal review
- **Preemptive Improvement**: Addressing likely quality concerns during generation
- **Review Readiness**: Preparing responses that are likely to meet assessment standards

### Performance Optimization

**Generation Efficiency**:
- **Template Utilization**: Leveraging response templates and patterns for efficiency
- **Information Organization**: Systematic organization of content for clarity and completeness
- **Language Optimization**: Efficient application of Parliamentary language standards
- **Resource Management**: Balancing thoroughness with processing efficiency

**Quality Enhancement**:
- **Continuous Learning**: Learning from feedback patterns to improve initial generation quality
- **Pattern Recognition**: Recognizing successful response patterns for replication
- **Standard Internalization**: Progressively better application of Parliamentary standards
- **Error Reduction**: Systematic reduction of common quality issues through learning

## Integration Architecture

### Input Processing

**Structured Information Integration**:
**Input**: Organized key elements from Key Elements Agent with themes, stakeholders, policies, and facts
**Processing**: Systematic synthesis of structured information into coherent Parliamentary response
**Quality**: Ensures comprehensive coverage of all important extracted elements

### Output Generation

**Response Delivery**:
**Format**: Parliamentary-standard response optimized for governmental communication
**Quality**: Meets formal language, content, and structural requirements
**Metadata**: Includes attempt tracking and improvement history for audit purposes

### Feedback Loop Integration

**Review Response Processing**:
**Input**: Detailed feedback from Review Agent with specific improvement guidance
**Processing**: Systematic analysis and integration of feedback for targeted improvement
**Output**: Enhanced response that addresses identified quality issues

## Performance Characteristics

### Quality Metrics

**Parliamentary Standards Compliance**: Percentage of responses meeting all Parliamentary criteria on each attempt
**Improvement Effectiveness**: Measurement of quality enhancement through iterative improvement cycles
**Feedback Integration Success**: Assessment of how effectively Review Agent feedback is incorporated
**Response Completeness**: Evaluation of how comprehensively responses address user queries

### Efficiency Measures

**Generation Speed**: Response generation time for initial and subsequent attempts
**Improvement Efficiency**: Speed and effectiveness of incorporating feedback for improvement
**Resource Utilization**: Computational resource usage across multiple attempts
**Completion Predictability**: Consistency of workflow completion within expected timeframes

The Response Agent represents the core content generation capability of our Parliamentary Questions analysis system, combining sophisticated Parliamentary standards compliance with iterative improvement mechanisms to ensure high-quality, appropriate governmental communication. Its design emphasizes both initial quality and systematic enhancement through feedback integration, resulting in responses that meet professional governmental communication requirements. 