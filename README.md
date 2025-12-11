# The-Trial-of-the-Sphinx
## System Overview

The system consists of three major components that work together to create the full gameplay experience.

### 1. World Layout

  The world is represented as a small graph of interconnected Location nodes.
  Each location specifies:

- Its neighboring rooms

- A description

- Items available to pick up

- Whether the room is blocked or contains a riddle

This creates a simple but deterministic world structure that supports puzzle-controlled progression.

### 2. Parser & Gameplay Logic

All gameplay logic is implemented in Python inside a single notebook.
The Parser handles:

- Interpreting player commands

- Managing movement between rooms

- Tracking inventory and item interactions

- Handling blocked rooms and riddle gating

- Managing lives, win conditions, and game-over states

- Displaying model-generated explanations

A lightweight Gradio interface provides clean and readable UI output.

### 3. AI-Generated Riddles

When the player enters a riddle room, the Parser prompts a fine-tuned Mistral model (via Unsloth) to produce a string containing:

- A riddle

- The correct answer

Player responses are evaluated using a cosine-similarity check, allowing natural language variation while still reliably detecting correct answers.

Together, these components form a compact but complete text-adventure loop that mixes deterministic room navigation with dynamic, AI-driven puzzle content.

## How to Set Up and Run the Demo
While running the code in colab, No need to install any packages manually.

pip install -r requirements.txt
### Run the demo
Run all the cells
- Candle Room, Start and EscapeRoom all contain Riddles
- While navigating rooms, the player may:
  
  Get a riddle
  
  answer it
  
  "Give up" and then it generates a new riddle.
  - The shortest winning path is:
    east->east->get->west->get->south->light->south->escape.
  

