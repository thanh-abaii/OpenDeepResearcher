# OpenDeepResearcher

## Overview
OpenDeepResearcher is an AI-powered research assistant that continuously searches for relevant information based on a user query until all necessary details are gathered. It leverages multiple AI and search APIs to automate and optimize the research process.

## Features
- **Iterative Research Loop**: The system refines its search iteratively until no further queries are required.
- **Asynchronous Processing**: Searches, webpage fetching, evaluation, and context extraction are performed concurrently for improved speed.
- **Duplicate Filtering**: Aggregates and deduplicates links within each round to avoid redundant processing.
- **LLM-Powered Decision Making**: Uses AI models to generate new search queries, decide page usefulness, extract relevant context, and produce a final comprehensive report.

## Technologies Used
### **1. Together AI**
- Generates precise search queries based on the user's topic.
- Default model: `deepseek-ai/DeepSeek-R1-Distill-Llama-70B`

### **2. Tavily API**
- Performs web scraping and extraction to retrieve content from relevant sources.

### **3. OpenAI (O1-Mini)**
- Generates the final long-form research report.

## Requirements
You will need API access and keys for:
- Together AI API
- Tavily API
- OpenAI API

### **Installation & Setup**
#### **1. Clone or Open the Notebook**
Download the notebook file or open it in **Google Colab**.

#### **2. Install Dependencies**
Run the following command in a Colab cell to install necessary libraries:
```python
!pip install aiohttp together tavily openai
```

#### **3. Configure API Keys**
Set up API keys securely in **Google Colab**:
```python
from google.colab import userdata
TOGETHER_API_KEY = userdata.get("TOGETHER_API_KEY")
TAVILY_API_KEY = userdata.get("TAVILY_API_KEY")
OPENAI_API_KEY = userdata.get("OPENAI_API_KEY")
```

## Usage
#### **1. Run the Notebook**
Execute all cells in order. The notebook will prompt you for:
- A **research query/topic**.
- An optional **maximum number of iterations** (default is **2** to prevent excessive API usage).

#### **2. Research Process**
1. **Initial Query & Search Generation**: Together AI generates initial search queries.
2. **Web Search & Content Extraction**: Tavily API performs searches, extracts content, and filters out irrelevant links.
3. **Iterative Refinement**: AI evaluates gathered data, determines if more research is needed, and refines search queries accordingly.
4. **Final Report Generation**: OpenAI (O1-Mini) compiles all relevant information into a **detailed and structured research report**.

#### **3. View the Final Report**
Once the research loop is complete, the final comprehensive report is generated and printed in the output.

## How It Works
### **1. Input & Query Generation**
- The user provides a research topic.
- Together AI generates up to **four** distinct search queries to maximize relevant results.

### **2. Concurrent Search & Processing**
- **Tavily API** performs searches for all queries asynchronously.
- Aggregates and deduplicates links within each iteration.
- Extracts webpage content and evaluates its relevance.

### **3. Iterative Refinement**
- If more data is needed, the system generates **new** search queries and repeats the process.
- The loop terminates when sufficient information is gathered or the iteration limit is reached.

### **4. Final Report Generation**
- OpenAI **O1-Mini** processes the collected context and generates a **long-form research report**.
- Ensures structured formatting and deep insights.

## Troubleshooting
#### **1. RuntimeError with asyncio**
If you encounter:
```
RuntimeError: asyncio.run() cannot be called from a running event loop
```
Ensure that you are using Google Colab and handling asynchronous execution properly.

#### **2. API Issues**
- Check your API keys and ensure they are correctly set up.
- Verify that you are not exceeding API rate limits.
- If OpenAI model `o1-mini` fails, ensure you have access by checking: [OpenAI API Models](https://api.together.ai/models).

## License
OpenDeepResearcher is released under the **MIT License**.

## Follow for Updates
Stay updated with AI research advancements by following me on [X (Twitter)](https://twitter.com).
