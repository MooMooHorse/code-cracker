# code-cracker
Code base cracker provides user with an intuitive interface to understand small to medium scaled code-base
1. Understand the purpose of the project (input, output, problem space, simplified data-path)
2. Easily see the main components and simplified workflow
    1. Zero-shot generation: without providing our module with any reference, our module can generate a visualization of the workflow, including summarized main logic, branches, and testing suggestions.
    2. few-shots generation: usually what users get to know a project is by dumping some intermediate values of some crucial variables. Our zero-shot generation can produce many suggestions as for how users can add those debugging / testing code. Provided with the results of those code, we will generate a more clear and simple workflow explanation
3. One-click install the prerequisite (for the studied projects, our input)
4. Go further by QA / testing with **minimum human effort** to fully understand the project in any depth(LLM assisted interaction)
    - The project aims to minimize the number of words you see
    - The project aims to minimize the number of characters you type
    - The project aims to minimize the number of mouse clicks
    - …
5. Support online / offline mode. (use cloud hosted / local LLMs’ APIs)
6. Be provided with an evaluation dataset so your PRs can be evaluated and efficiently merged.

# Why code cracker?

There are existing tools & research work to:

1. Code snippet summary and completion [R(esearch) & E(ngineering)]
2. Knowledge graph extraction and application from code-base [R & E]
3. Meta-knowledge extraction from various data-source [R & E]
4. Neo4j storage and visualization [R & E]
5. Framework for AI app [R & E]
6. Automatic test generation [R & E]

**As an user, I demand**:

**Simple and easy interface to understand code-base**

There are 3 pieces missing:

1. **Engineering effort** to put SOTA pieces together for **user experience** on medium scaled code-bases.
2. **Safe, flexible and SOTA** LLM integration.
3. **Open source** an **AI app** that fully satisfy the need of users to understand a **code-base**

# Features

1. Understand **structured, medium-scaled** code-bases.
2. Efficiently utilize high-quality **data sources**, such as **git commit history**, **code dependencies**, etc.
3. **Interactive:** through both discussion (QA) and code **injection** (testNrun)
4. Prompt users with **learning ideas**
5. Pinpoint the **reference** to any answers
6. Focus on **usefulness and simplicity** (a pure engineering work not research work)
7. **Safe** (switch between online / offline) and **up-to-date** (freedom to switch between SOTA models)
8. An **evaluation dataset** to prove the effectiveness and provide tuning basis.

# Layer 1: code cracker library

python package(will publish to https://packaging.python.org/en/latest/tutorials/packaging-projects/) 

Keywords: **Large Language Model(LLM) + Knowledge Extraction(KG)**

The library will contains all functions for the following workflow.

## Knowledge extraction

<aside>
💡 Code-base simplification workflow

1. Meta-knowledge extraction
    - git commit history extraction
    - code dependency extraction
2. Knowledge graphs extraction ← (meta-knowledge, and code-base) [code KG, learn KG]
    - code KG is a knowledge graph based on code-base and their meta-knowledge
    - learn KG is a knowledge graph based on external material such as books for users to have more insights on code-base.
3. Create simplification variants KG
</aside>

## Knowledge application

<aside>
💡 QA workflow

1. Create idea/question [data source: simplified code KG, learn KG]
2. Create summarized answer [data source: simplified code KG, learn KG]
3. Find reference [data source: simplified code KG, learn KG]
</aside>

<aside>
💡 Code Injection workflow [Target language: Python / JS / TS]

1. Create Motivation / Prompted with motivation [data source: common motivation + code KG] 
2. Get test-bed
3. Generate tests
4. Run tests
5. Iterative improve tests
</aside>

## Knowledge update

<aside>
💡 Code-base simplification enhanced workflow

1. Human-label extraction
2. Knowledge graph update ← (data source: simplified code KG, learn KG and user interaction trace)
</aside>

## Knowledge Storage Format

<aside>
💽 Different storage formats for knowledge graphs

- Node
    - reference
    - knowledge
    - link
    
- Reference
    - type
    - file path
    - content
    
- Knowledge
    - type
    - content
    
- link
    - type
    - src_node
    - dest_node
    
</aside>

# Layer 2: code cracker app back-end + Beta-level code cracker app

The back-end will orchestrate the functions in the library this can be perfectly solved by using [Dify](https://github.com/langgenius/dify), an AI-app building framework.

# Layer 3: Production-level code cracker web app

[llama-webui](https://github.com/open-webui/open-webui)/[fast api](https://github.com/tiangolo/fastapi)/[vscode](https://github.com/sxei/vscode-plugin-demo?tab=readme-ov-file)
