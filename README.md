# LLM Routing System - Next League

## Overview
A Next League branded LLM interface that analyzes user prompts and routes them to the most relevant LLM(s) based on topic analysis and learning from user feedback.

## Problem Statement
It's difficult to know which LLM is best suited for a given task. Different LLMs excel at different domains (finance, tech stack, design, strategy, marketing, etc.), but users often don't know which one to choose.

## Solution Architecture

### Core Components
1. **User Interface**: Single text box for prompt input
2. **Operator LLM**: Analyzes prompts and routes to appropriate LLMs
3. **Tag-Based Routing System**: Maps topics to LLM strengths
4. **Feedback System**: Collects user votes to improve routing
5. **Learning Database**: Stores tag ↔ LLM mapping data

## Flow Diagram

```mermaid
flowchart TD
    A[User enters prompt] --> B[Operator LLM analyzes prompt]
    B --> C{Topics identified?}
    
    C -->|Yes| D[Check tag database]
    C -->|No| E[Select 2 random LLMs]
    
    D --> F{Best-matching LLMs found?}
    F -->|Yes| G[Route to best-matching LLMs]
    F -->|No| E
    
    E --> H[LLMs generate responses]
    G --> H
    
    H --> I{Multiple responses?}
    I -->|Yes| J[Display responses to user]
    I -->|No| K[Display single response]
    
    J --> L[User votes on better answer]
    L --> M[Store vote data]
    M --> N[Update tag ↔ LLM mapping]
    
    K --> O[End]
    N --> O
    
    style A fill:#e1f5fe
    style B fill:#fff3e0
    style D fill:#f3e5f5
    style E fill:#f3e5f5
    style L fill:#e8f5e8
    style M fill:#e8f5e8
    style N fill:#e8f5e8
```

## Detailed Process Flow

### 1. Prompt Analysis
- User submits prompt through single text box
- Operator LLM analyzes the prompt content
- Identifies relevant topics and domains

### 2. Routing Decision
- **If topics are identified**: Check existing tag database for best-matching LLMs
- **If no topics found**: Select 2 random LLMs for comparison

### 3. Response Generation
- Selected LLM(s) generate responses to the user's prompt
- Responses are presented to the user

### 4. Feedback Collection
- If multiple responses are shown, user votes on the better answer
- Vote data is stored for learning purposes

### 5. Learning & Improvement
- Vote data is used to refine the tag ↔ LLM mapping
- Database is updated with new insights about LLM performance

## Tag Categories

The system recognizes and routes based on these topic categories:

- **Finance**: Financial analysis, investment advice, accounting
- **Tech Stack**: Programming, software development, technical architecture
- **Design**: UI/UX, graphic design, creative direction
- **Strategy**: Business strategy, planning, decision-making
- **Marketing**: Digital marketing, branding, customer acquisition
- **Research**: Data analysis, market research, academic topics
- **Writing**: Content creation, copywriting, documentation
- **General**: Broad topics, general knowledge, miscellaneous
