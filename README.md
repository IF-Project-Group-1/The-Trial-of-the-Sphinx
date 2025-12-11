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

2. Parser & Game Engine

All gameplay logic is implemented in Python inside a single notebook.
The Parser handles:

Interpreting player commands

Managing movement between rooms

Tracking inventory and item interactions

Handling blocked rooms and riddle gating

Managing lives, win conditions, and game-over states

Displaying model-generated explanations

A lightweight Gradio interface provides clean and readable UI output.

3. AI-Generated Riddles

When the player enters a riddle room, the Parser prompts a fine-tuned Mistral model (via Unsloth) to produce a JSON bundle containing:

A riddle

Three hints

The correct answer

A short explanation

Player responses are evaluated using a cosine-similarity check, allowing natural language variation while still reliably detecting correct answers.

Together, these components form a compact but complete text-adventure loop that mixes deterministic room navigation with dynamic, AI-driven puzzle content.
