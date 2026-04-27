<h1 align="center">Multi-Agent AI Debate System with LangChain</h1>

Welcome to the Multi-Agent AI Debate System! This project showcases a fascinating application of LangChain where two AI agents engage in a structured debate, and a third AI agent acts as a neutral judge to evaluate their arguments.

## ✨ Features

-   **Dynamic Debate**: Two specialized AI agents (`Agent A` advocating FOR a topic and `Agent B` arguing AGAINST it) engage in a debate.
-   **Structured Arguments & Rebuttals**: Agents provide initial arguments and then respond to each other's points in rebuttal rounds.
-   **Impartial AI Judge**: A dedicated `Judge` agent evaluates the debate based on logic, clarity, and persuasiveness, providing scores and declaring a winner.
-   **JSON Output**: The judge's decision, scores, reason, and summary are provided in a clean, parseable JSON format.
-   **Modular & Extensible**: Built with LangChain's powerful expression language, making it easy to understand and extend.

## 🚀 Getting Started

This project is designed to run seamlessly in Google Colab.

### 🔑 API Key Setup (Groq)

To use the language models, you'll need an API key from Groq. Follow these steps to configure it securely:

1.  **Obtain a Groq API Key**: Visit the [Groq Console](https://console.groq.com/) and generate a new API key.
2.  **Add to Colab Secrets**: In your Google Colab notebook, click on the "🔑 Secrets" icon in the left sidebar.
3.  **Create a New Secret**: Add a new secret with the name `GROQ_API_KEY`.
4.  **Paste Your Key**: Paste your generated Groq API key into the "Value" field.
5.  **Enable Notebook Access**: Make sure to toggle "Notebook access" **on** for this secret.

### 📦 Installation

The necessary Python packages can be installed directly within the Colab environment. The notebook includes a cell that runs:

```python
%pip install --quiet langchain-core langchain-community langchain-google-genai langchain-groq
```

### ▶️ How to Run the Debate

1.  **Open in Google Colab**: Upload or open this notebook in Google Colab.
2.  **Configure API Key**: Follow the API Key Setup steps above.
3.  **Run All Cells**: Execute all code cells in the notebook sequentially.
4.  **Define Your Topic**: You can easily change the `debate_topic` variable in the last code cell to kick off a new debate:

    ```python
    if __name__ == "__main__":
        debate_topic = "Is AI dangerous?" # <-- Change this!
        final_result = run_debate(debate_topic, llm, agent_a_prompt, agent_b_prompt, rebuttal_prompt, judge_prompt)
    ```

## 🏗️ Code Structure

The system is organized into clear, functional components:

-   **`llm` Initialization**: Sets up the chosen LLM (currently Groq's `mixtral-8x7b-32768`).
-   **Prompt Templates**: Distinct `ChatPromptTemplate` instances for Agent A, Agent B, Rebuttals, and the Judge, ensuring clear instructions for each role.
-   **Modular Functions**: 
    -   `generate_argument()`: Crafts initial arguments for each agent.
    -   `generate_rebuttal()`: Formulates responses to the opponent's arguments.
    -   `judge_debate()`: Analyzes the entire debate and provides a structured judgment.
-   **`run_debate()`**: The main orchestrator function that manages the debate flow, prints outputs, and returns the final judgment.

## 📊 Example Output

When you run the debate with the topic "Is AI dangerous?", you'll see a detailed log of arguments and rebuttals, culminating in a structured final judgment like this (output details will vary based on LLM responses):

```
======================================================================
                             DEBATE TOPIC                             
                        -- YOUR TOPIC --                        
======================================================================

Generating initial argument for Agent A (FOR)...
...
-------------------- Agent A (FOR) Initial Argument --------------------
[Agent A's argument]

Generating initial argument for Agent B (AGAINST)...
...
-------------------- Agent B (AGAINST) Initial Argument --------------------
[Agent B's argument]

Generating rebuttal for Agent A (FOR)...
...
-------------------- Agent A (FOR) Rebuttal to Agent B --------------------
[Agent A's rebuttal]

Generating rebuttal for Agent B (AGAINST)...
...
-------------------- Agent B (AGAINST) Rebuttal to Agent A --------------------
[Agent B's rebuttal]

Judging the debate...

======================================================================
                            FINAL JUDGMENT                            
======================================================================

Winner: A

Scores:
  Agent A: Logic=9, Clarity=9, Persuasion=8
  Agent B: Logic=7, Clarity=8, Persuasion=7

Reason: Agent A presented a more comprehensive and nuanced argument...

Summary: The debate centered on the potential dangers of AI, with Agent A arguing...

======================================================================
```

Feel free to experiment with different topics and observe how the AI agents tackle complex issues!
