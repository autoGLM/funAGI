# funAGI
fundamental AGI point of departure logic.py and SocraticReasoning.py
debug environment with logging
to do: include SimpleMind.py neural network and coach.py training

FundamentalAGI Project Setup

codebase to create a simplified version called fundamentalAGI.py. This new script will use SocraticReasoning.py and logic.py with verbose logging to understand the export of the belief into ./memory/truth. This simplified version will omit reasoning.py and directly leverage the core logic and memory management. Here's how we will structure the project:

    fundamentalAGI.py: Main script to run the AGI.
    agi.py: Core AGI logic.
    api.py: API key management.
    bdi.py: BDI (Belief-Desire-Intention) model.
    chatter.py: Interface for different chat models.
    logic.py: Logic table management and evaluation.
    memory.py: Memory management for storing dialogues and truth values.
    SocraticReasoning.py: Socratic reasoning engine for the AGI.

# agi.py AGI workflow

    API Key Management (api.py):

    Loads API keys from api_keys.json or environment variables.
    Manages adding, removing, and listing API keys.

Core AGI Logic (agi.py):

    Initializes the AGI with API manager and chatter models.
    Learns from data by creating propositions.
    Makes decisions by leveraging SocraticReasoning.

Memory Management (memory.py):

    Handles creating necessary directories.
    Stores and loads conversation memories.
    Stores valid truths and dialogue entries.

Socratic Reasoning (SocraticReasoning.py):

    Manages premises and draws logical conclusions.
    Logs actions and results.
    Validates conclusions using LogicTables.

Logic Table Management (logic.py):

    Manages logic variables, expressions, and truth tables.
    Evaluates expressions and validates truths.
    Logs all actions and saves beliefs.

Chat Models (chatter.py):

    Interfaces for different chat models like GPT4o, GroqModel, and OllamaModel.

# Key Components and Flow

    API Key Management:
        APIManager class handles loading, saving, and managing API keys.
        In EasyAGI.__init__, the user is prompted to manage API keys if necessary.

    Learning from Data:
        AGI.learn_from_data method processes input data into two propositions.
        These propositions are added as premises to the SocraticReasoning engine.

    Making Decisions:
        AGI.make_decisions method invokes the Socratic reasoning process to draw a conclusion.
        The conclusion (decision) is returned.

    Main Loop:
        EasyAGI.main_loop handles user input and processes it using the AGI system.
        Decisions are communicated back to the user and stored in short-term memory.


Belief-Desire-Intention Model (bdi.py):

    Manages beliefs, desires, and intentions.
    Processes BDI components for decision making.


    funAGI.py is the UI. fundatmentalAGI funAGI has been published to showcase, audit and debug the easyAGI SocraticReasoning.py and logic.py
#########################################################################
# Process Flow from User Input to Response
Step 1: User Input

    Action: The user provides an input via the command line.
    Input Example: "Explain the workflow to building AGI"

Step 2: Perceive Environment

    Method: EasyAGI.perceive_environment
    Action: The system captures the user's input.
    Output: The user's input string is returned for processing.

Step 3: Learning from Data

    Method: AGI.learn_from_data
    Action: The user's input string is processed to extract propositions.
    Process:
        The input string is split into two propositions based on a delimiter (e.g., ";").
        If the input contains only one proposition, the second proposition is set as an empty string.
        The propositions are added as premises in the Socratic reasoning engine.
    Output: Two propositions are returned for further processing.

    Adding Premises to Socratic Reasoning:
        Validates and adds each proposition as a premise.
        Logs each addition.

    Processing THOT:
        Iterates through reasoning methods.
        Generates intermediate conclusions.
        Aggregates combined results.

    Logging THOT Data:
        Logs premises, combined results, and final decision.
        Appends to THOT log file (thots.json).

    Drawing a Conclusion:
        Generates logical conclusion using language model.
        Validates conclusion.
        Logs conclusion.

    Communicating Response:
        Prints final decision to console.
        Logs communicated response.

    Storing Conversation Memory:
        Creates DialogEntry with input and decision.
        Saves entry to STM.

This workflow provides a comprehensive view of how user input is processed, reasoned with, and responded to in fundamentalAGI funAGI.py system. Each component plays a critical role in ensuring the AGI provides accurate and logical responses based on the input provided.
################################################################

```csharp
+-------------------+       +-------------------+       +---------------------+
|    User Input     | ----> | Perceive          | ----> | Learning from Data  |
| (Command Line)    |       | Environment       |       | (Extract Propositions)|
+-------------------+       +-------------------+       +---------------------+
                                      |
                                      v
                             +-------------------+
                             | Add Premises to   |
                             | Socratic Reasoning|
                             +-------------------+
                                      |
                                      v
                             +-------------------+
                             |  Process THOT     |
                             |  (Various Reasoning|
                             |   Techniques)      |
                             +-------------------+
                                      |
                                      v
                             +-------------------+
                             |  Log THOT Data    |
                             +-------------------+
                                      |
                                      v
                             +-------------------+
                             |  Draw Conclusion  |
                             |  (GPT-4 Model)    |
                             +-------------------+
                                      |
                                      v
                             +-------------------+
                             |Communicate Response|
                             |  to User           |
                             +-------------------+
                                      |
                                      v
                             +-------------------+
                             | Store Conversation |
                             | Memory (STM)       |
                             +-------------------+
```

install (builds an openai API and groq API ready terminal interaction from openai or groq API key with response from SocraticReasoning.py and logic.py with logging to local folders from memory.py)

```bash
git clone https://github.com/autoGLM/funAGI/
cd funAGI
python3 -m venv fun
source fun/bin/activate
pip install -r requirements.txt
python3 funAGI.py
```


