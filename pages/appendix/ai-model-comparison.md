---
layout: default
title: AI Model Comparison
parent: Appendix
---

# AI Model Comparison

## Comparison of OpenAI, Anthropic, and Local LLM Models

We conducted a comparative evaluation of OpenAI's GPT models, Anthropic's Claude models, and locally hosted open-source models, focusing on their capabilities, integration potential, and suitability for departmental use.

## OpenAI Models

OpenAI's GPT model family comprises a range of models tailored for various use cases. For example:

The Omni series (denoted as "o" followed by a number) supports chain-of-thought reasoning, which improves its ability to connect facts with logical conclusions.

The Mini and Mini-High series are smaller, distilled models that preserve most reasoning and functional capabilities while offering advantages in cost-efficiency, reduced carbon emissions, and faster response times.

We selected OpenAI's models for our evaluation as they have traditionally led the field in natural language processing and reasoning tasks. Using these models provided a strong benchmark and a practical head start for providing value quickly.

## Anthropic Models

Anthropic's Claude models are primarily available in two variants: Sonnet and Haiku, indicating different model sizes and capabilities.

Unlike OpenAI's more complex ecosystem, Claude Sonnet models are simply numbered, with Claude 4 introducing chain-of-thought reasoning.

Claude 4 exhibits strong performance in code generation tasks and appears more optimised for programming-related workflows than GPT. However, it remains broadly competitive, and Anthropic seems to be rapidly closing the gap with each new release.

## Local Models

Deploying local LLMs allows for complete ownership of model weights and ensures data privacy. This approach eliminates reliance on external APIs and provides full control over data flow.

While most local models currently lag behind commercial offerings in overall capability, especially in structured tasks, this is improving. Additionally, they often lack advanced features like structured output generation, which can affect usability when chaining LLM outputs with traditional coding logic.

## Considerations for DEFRA

Currently, DEFRA has Anthropic models deployed via AWS Bedrock through CDP. A recommended next step would be to conduct a detailed comparison of outputs between OpenAI and Anthropic models in our operational environment. This could help identify which model family best supports specific departmental needs. 