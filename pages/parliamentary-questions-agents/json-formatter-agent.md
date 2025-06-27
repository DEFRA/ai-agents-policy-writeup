---
layout: default
title: JSON Formatter Agent
parent: Parliamentary Questions Agentic Workflow
---

# JSON Formatter Agent

## Overview
The JSON Formatter Agent serves as the final output generation layer in our Parliamentary Questions workflow, transforming approved responses into comprehensively structured, API-ready JSON format with complete audit trails, processing metadata, and integration-ready formatting for downstream consumption and analysis.

## Prompt Instructions & Agent Behavior

### Core Prompt Mission
The JSON Formatter Agent operates as a **specialized agent that formats conversational AI responses into structured JSON output for API consumption**. The prompt positions the agent as a technical formatter responsible for converting complex processing information into standardized, machine-readable output.

### Specific Task Instructions
The prompt provides clear formatting directives:

**Primary Task**: Convert provided information into a well-structured JSON object that follows an exact schema, extracting key information, summarizing search results, and presenting a clean final answer.

### JSON Schema Requirements
The prompt mandates adherence to a specific schema structure:

**Core Schema Elements**:
```json
{
  "query": "<string>",                         // the user's original search or question
  "semantic_search": {
    "total_results": <integer>,                // number of hits returned
    "results": [
      {
        "id": "<string|integer>",              // PQ ID from the original parliamentary question
        "question": "<string>",                // source question text
        "answer": "<string>",                  // source answer text
        "score": <float>                       // similarity/relevance score
      }
    ]
  },
  "key_information": [
    "<string>"                                 // distilled fact with PQ reference and date
  ],
  "final_answer": "<string>",                  // crafted, human-readable response without PQ references
  "parliamentary_review": {
    "attempts": <integer>,                     // number of review attempts made
    "status": "<string>",                      // "PASSED" or "FAILED"
    "assessment": "<string>"                   // full review assessment output
  }
}
```

### Processing Instructions
The prompt specifies a 6-step processing methodology:

**Step 1 - Extract Query**: Use the exact user question provided without modification
**Step 2 - Process Search Results**: Convert raw search data into the semantic_search structure while preserving original PQ IDs
**Step 3 - Distill Key Information**: Extract 3-5 key facts from the AI response as bullet points, including PQ references with dates where information is cited
**Step 4 - Format Final Answer**: Use the AI response as the final_answer field, but remove any PQ references from this section
**Step 5 - Include Parliamentary Review**: Extract review attempt count, status (PASSED/FAILED), and full assessment from the review data
**Step 6 - Preserve IDs**: Use the actual PQ IDs provided in the search results, not generated ones

### Critical Output Requirements
The prompt establishes strict formatting standards:

**Output Format Mandates**:
- **Pure JSON Only**: Return ONLY valid JSON - no markdown formatting, no code blocks, no additional text
- **No Code Block Wrapping**: Do NOT wrap in ```json or ``` blocks
- **Direct JSON Output**: Start directly with { and end with }
- **Proper Escaping**: Ensure all string values are properly escaped
- **Null Handling**: Use null for missing optional fields
- **Schema Adherence**: Maintain exact field names and structure as specified

**Format Example**: The prompt provides a specific example of correct output format:
```json
{"query": "example question", "semantic_search": {"total_results": 2, "results": [{"id": 1, "question": "...", "answer": "...", "score": 0.95}]}, "key_information": ["fact 1", "fact 2"], "final_answer": "complete answer", "parliamentary_review": {"attempts": 1, "status": "PASSED", "assessment": "review details"}}
```

### Data Processing Specifications

**Information Extraction Requirements**:
- **Query Preservation**: Extract and preserve the exact user question as provided
- **Search Data Conversion**: Transform raw search results into structured semantic_search format
- **ID Preservation**: Maintain original Parliamentary Question IDs from search results
- **Key Information Distillation**: Extract 3-5 key facts with PQ references and dates
- **Answer Cleaning**: Remove PQ references from final answer while preserving content
- **Review Data Integration**: Include complete Parliamentary review information

**Content Transformation Rules**:
- **Reference Removal**: Strip PQ references from final answer text while maintaining in key_information
- **Date Integration**: Include PQ references with dates in key_information sections
- **Status Mapping**: Convert review outcomes to "PASSED" or "FAILED" status
- **Score Preservation**: Maintain original similarity/relevance scores from search results

### British English Compliance
The prompt mandates **British English spelling and grammar conventions** for all text content in the JSON output, ensuring consistency with Parliamentary standards and maintaining appropriate governmental language use throughout the formatting process.

### Data Integrity Requirements
The prompt emphasizes critical data preservation principles:

**Original Data Preservation**:
- **ID Accuracy**: Use actual PQ IDs provided in search results, not fabricated identifiers
- **Content Fidelity**: Maintain accuracy of search result content and metadata
- **Review Completeness**: Include complete review assessment information
- **Query Integrity**: Preserve exact user query without modification

**Structure Consistency**:
- **Schema Compliance**: Rigid adherence to specified JSON schema structure
- **Field Completeness**: Ensure all required fields are populated appropriately
- **Type Consistency**: Maintain specified data types for all fields
- **Format Standardization**: Consistent formatting across all output instances

### Error Prevention Instructions
The prompt provides specific guidance to prevent common formatting errors:

**Technical Precision Requirements**:
- **JSON Validity**: Ensure output is valid, parseable JSON
- **Syntax Accuracy**: Proper JSON syntax with correct escaping and formatting
- **Field Validation**: Verify all required fields are present and correctly populated
- **Type Verification**: Ensure all values match specified data types

**Content Accuracy Safeguards**:
- **Source Verification**: Validate that output accurately reflects input information
- **Completeness Checking**: Ensure no critical information is lost during formatting
- **Reference Accuracy**: Maintain accuracy of all PQ references and dates
- **Status Consistency**: Ensure review status accurately reflects assessment outcomes

## Technical Design Philosophy

### Why Structured JSON Output?

**API Integration Requirements**:
- **Machine Readability**: JSON format enables programmatic consumption by external systems
- **Standard Compliance**: Industry-standard format for web APIs and system integration
- **Parsing Efficiency**: Structured format enables efficient data extraction and processing
- **Schema Validation**: Consistent structure allows for automated validation and verification

**System Integration Benefits**:
- **Microservices Compatibility**: JSON format integrates seamlessly with modern microservices architectures
- **Database Storage**: Structured format enables efficient storage in document databases
- **Analytics Pipeline**: Formatted output feeds directly into data analysis and reporting systems
- **User Interface Integration**: Structured data enables dynamic UI generation and presentation

### Why Comprehensive Audit Trails?

**Accountability and Transparency**:
- **Process Visibility**: Complete documentation of all processing steps and decisions
- **Quality Assurance**: Detailed evidence of quality assessment and improvement processes
- **Debugging Support**: Comprehensive information for troubleshooting and optimization
- **Compliance Documentation**: Evidence of appropriate Parliamentary standards application

**Historical Preservation**:
- **Response Evolution**: Complete genealogy of response development and improvement
- **Decision Documentation**: Record of all agent decisions and routing choices
- **Performance Analysis**: Data for system performance evaluation and optimization
- **Learning Integration**: Historical data for system improvement and pattern recognition

### Why Final-Stage Formatting?

**Processing Efficiency**:
- **Specialized Function**: Dedicated formatting agent optimizes for output structure and completeness
- **Resource Management**: Final-stage formatting prevents repeated structuring overhead during processing
- **Error Prevention**: Centralized formatting reduces the risk of inconsistent output structures
- **Quality Control**: Final formatting stage enables comprehensive output validation

**Integration Optimization**:
- **Consumer-Focused Design**: Output structure optimized for downstream consumption requirements
- **Metadata Enrichment**: Addition of processing metadata that enhances output value
- **Version Control**: Consistent versioning and schema management for API evolution
- **Documentation Integration**: Embedded documentation for API consumers

## Primary Function
Converts final response into structured JSON format including complete audit trail, search results, response attempts, and review feedback for API consumption while preserving comprehensive processing metadata and ensuring consistent output formatting.

## Technical Implementation

### JSON Structure Architecture

**Hierarchical Information Organization**:
The JSON Formatter creates a sophisticated, multi-layered structure that preserves all critical processing information:

**Core Response Structure**:
- **Primary Content**: User query and final Parliamentary-standard response
- **Processing Results**: Search results, filtered content, and extracted key elements
- **Quality Assurance**: Complete review process documentation and assessment results
- **Metadata**: Processing timestamps, performance metrics, and system information

**Nested Data Organization**:
- **Response Genealogy**: Complete history of response attempts and improvements
- **Review Documentation**: Detailed assessment results and feedback across all attempts
- **Processing Pipeline**: Step-by-step documentation of agent processing
- **System Metadata**: Technical information about processing environment and configuration

### Comprehensive Audit Trail Implementation

**Response Evolution Tracking**:
**Technical Implementation**: Systematic documentation of every response attempt with metadata
**Information Preserved**:
- **Attempt Sequence**: Chronological order of response generation attempts
- **Content Evolution**: Full text of each response attempt for comparison
- **Word Count Progression**: Length optimization tracking across attempts
- **Timestamp Documentation**: Precise timing of each generation attempt

**Review Process Documentation**:
**Technical Implementation**: Complete preservation of quality assessment cycles
**Information Preserved**:
- **Assessment Details**: Full breakdown of each review against Parliamentary criteria
- **Feedback History**: All improvement suggestions provided across iterations
- **Pass/Fail Decisions**: Clear documentation of assessment outcomes
- **Criteria Evaluation**: Detailed scoring against each Parliamentary standard

**Processing Metadata Preservation**:
**Technical Implementation**: Comprehensive capture of system processing information
**Information Preserved**:
- **Agent Processing**: Timing and results from each agent in the workflow
- **Search Performance**: Semantic search execution metrics and result quality
- **Error Handling**: Documentation of any processing issues and recovery mechanisms
- **System Configuration**: Technical environment and configuration information

### Advanced Formatting Features

**Schema Consistency Management**:
- **Version Control**: Consistent schema versioning for API evolution management
- **Backward Compatibility**: Structured approach to maintaining compatibility across schema updates
- **Validation Integration**: Built-in schema validation to ensure output consistency
- **Documentation Embedding**: Self-documenting JSON structure with embedded field descriptions

**Output Optimization**:
- **Data Efficiency**: Optimized structure that balances completeness with transmission efficiency
- **Nested Organization**: Logical grouping of related information for easy consumption
- **Index Generation**: Creation of summary indices for rapid information access
- **Compression Readiness**: Structure optimized for efficient compression when needed

## Output Structure

### Core Response Data

**Primary Information Block**:
```json
{
  "question": "Original user query with complete context",
  "response": "Final Parliamentary-standard response text",
  "response_metadata": {
    "word_count": 185,
    "generation_attempt": 2,
    "review_status": "PASSED",
    "processing_time_ms": 3240
  }
}
```

**Search and Processing Results**:
```json
{
  "search_results": [
    {
      "question_text": "Parliamentary Question content",
      "similarity_score": 0.89,
      "metadata": {
        "session": "2023-24",
        "date": "2024-01-15",
        "department": "Department for Environment"
      }
    }
  ],
  "filtered_results": [...],
  "key_elements": {
    "themes": [...],
    "stakeholders": [...],
    "policies": [...],
    "timeline": [...]
  }
}
```

### Parliamentary Review Metadata

**Comprehensive Review Documentation**:
```json
{
  "parliamentary_review": {
    "total_attempts": 2,
    "final_status": "PASSED",
    "all_attempts": [
      {
        "attempt": 1,
        "response": "First response attempt content",
        "review_passed": false,
        "assessment": "Detailed assessment text",
        "feedback": "Specific improvement suggestions",
        "timestamp": "2024-01-15T10:30:00Z"
      },
      {
        "attempt": 2,
        "response": "Improved response content",
        "review_passed": true,
        "assessment": "Final assessment confirming standards compliance",
        "feedback": null,
        "timestamp": "2024-01-15T10:32:00Z"
      }
    ],
    "final_assessment": "Complete final review assessment text"
  }
}
```

### Complete Audit Trail

**Processing History Documentation**:
```json
{
  "response_attempts": [
    {
      "attempt": 1,
      "response": "Full text of first response attempt",
      "timestamp": "2024-01-15T10:30:00Z",
      "word_count": 165,
      "review_passed": false,
      "review_assessment": "Detailed assessment",
      "review_feedback": "Specific improvement guidance"
    }
  ],
  "feedback_history": [
    "Attempt 1: Improve Parliamentary language formality",
    "Attempt 1: Ensure word count within 150-200 range"
  ],
  "processing_metadata": {
    "workflow_start": "2024-01-15T10:28:00Z",
    "workflow_end": "2024-01-15T10:33:00Z",
    "total_processing_time_ms": 5000,
    "agent_performance": {
      "search_agent": { "execution_time_ms": 800 },
      "filter_agent": { "execution_time_ms": 600 },
      "key_elements_agent": { "execution_time_ms": 900 },
      "response_agent": { "execution_time_ms": 2400 },
      "review_agent": { "execution_time_ms": 1200 },
      "json_formatter_agent": { "execution_time_ms": 100 }
    }
  }
}
```

## Advanced Features

### Metadata Enrichment

**Processing Performance Metrics**:
- **Agent Timing**: Individual execution time for each agent in the workflow
- **Quality Metrics**: Assessment scores and improvement progression tracking
- **Resource Utilization**: Memory and computational resource usage statistics
- **Error Documentation**: Any processing issues encountered and resolution methods

**Quality Assurance Documentation**:
- **Standards Compliance**: Detailed documentation of Parliamentary standards adherence
- **Review Progression**: Evolution of quality assessment across multiple attempts
- **Improvement Effectiveness**: Measurement of feedback integration success
- **Final Quality Confirmation**: Comprehensive documentation of final quality status

### Integration Support Features

**API Consumer Assistance**:
- **Schema Documentation**: Embedded field descriptions and usage guidance
- **Version Information**: API version and compatibility information
- **Response Codes**: Standard HTTP response codes and status indicators
- **Error Handling**: Structured error information for debugging and recovery

**Analytics Integration**:
- **Performance Indicators**: Key metrics for system performance analysis
- **Quality Trends**: Historical quality improvement patterns
- **Usage Statistics**: Information for usage pattern analysis and optimization
- **Compliance Reporting**: Data for Parliamentary standards compliance reporting

## Quality Assurance Mechanisms

### Output Validation

**Structure Verification**:
- **Schema Compliance**: Automated validation against defined JSON schema
- **Field Completeness**: Verification that all required fields are present and populated
- **Data Type Consistency**: Ensuring all fields contain appropriate data types
- **Nested Structure Validation**: Verification of complex nested object integrity

**Content Quality Assurance**:
- **Information Completeness**: Ensuring all processing results are captured in output
- **Audit Trail Completeness**: Verification that complete processing history is preserved
- **Metadata Accuracy**: Validation of processing metadata accuracy and completeness
- **Consistency Verification**: Ensuring consistency between different sections of output

### Error Prevention

**Formatting Error Handling**:
- **JSON Syntax Validation**: Ensuring valid JSON syntax in all output
- **Encoding Consistency**: Proper character encoding for international content
- **Escape Sequence Handling**: Appropriate escaping of special characters
- **Size Limit Management**: Ensuring output remains within reasonable size limits

**Data Integrity Protection**:
- **Information Preservation**: Protecting against data loss during formatting
- **Relationship Maintenance**: Preserving relationships between different data elements
- **Temporal Consistency**: Ensuring timestamp accuracy and consistency
- **Reference Integrity**: Maintaining valid references between related data elements

## Performance Optimization

### Output Efficiency

**Structure Optimization**:
- **Compression Readiness**: JSON structure optimized for efficient compression
- **Transmission Efficiency**: Balanced structure that minimizes bandwidth usage
- **Parsing Optimization**: Structure designed for efficient client-side parsing
- **Memory Efficiency**: Optimized for efficient memory usage during processing

**Processing Speed**:
- **Template Utilization**: Efficient use of JSON templates for consistent formatting
- **Streaming Support**: Capability for streaming large outputs when necessary
- **Caching Integration**: Potential for caching formatted structures for similar queries
- **Parallel Processing**: Concurrent formatting of independent output sections

### Scalability Considerations

**High-Volume Processing**:
- **Batch Formatting**: Efficient handling of multiple output formatting requests
- **Resource Management**: Optimized resource usage for high-throughput scenarios
- **Memory Management**: Efficient memory allocation and cleanup for large outputs
- **Performance Monitoring**: Built-in performance monitoring for optimization feedback

## Integration Architecture

### Input Processing

**Response Integration**:
**Input**: Final approved response from Review Agent with complete processing state
**Processing**: Systematic extraction and organization of all processing information
**Validation**: Ensuring all required information is available for complete output generation

### Output Delivery

**API-Ready Output**:
**Format**: Comprehensive JSON structure optimized for API consumption
**Quality**: Complete audit trail with all processing metadata preserved
**Compatibility**: Standard format compatible with web APIs and system integration

### Consumer Support

**Documentation Integration**:
- **Schema Documentation**: Complete API documentation embedded in output structure
- **Usage Examples**: Example consumption patterns for different use cases
- **Integration Guides**: Guidance for integrating with common systems and frameworks
- **Version Migration**: Support for migrating between different schema versions

## Performance Characteristics

### Output Quality

**Completeness Metrics**: Percentage of processing information successfully captured in output
**Accuracy Verification**: Validation of output accuracy against processing state
**Schema Compliance**: Adherence to defined JSON schema standards
**Integration Readiness**: Suitability for immediate consumption by downstream systems

### System Efficiency

**Formatting Speed**: Time required to generate complete JSON output from processing state
**Memory Utilization**: Memory efficiency during output generation and validation
**Output Size Optimization**: Balance between completeness and transmission efficiency
**Error Rate**: Frequency of formatting errors and validation failures

The JSON Formatter Agent represents the critical output generation capability of our Parliamentary Questions analysis system, transforming complex processing results into structured, API-ready format with comprehensive audit trails and integration support. Its design ensures complete information preservation while optimizing for downstream consumption and system integration requirements. 