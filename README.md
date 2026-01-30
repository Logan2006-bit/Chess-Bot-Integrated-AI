# Chess-Bot-Integrated-AI
Terminal Chess Engine with Human & AI Players

A modular, terminal-based chess engine written in Python that supports human vs human, human vs AI, and AI vs AI gameplay.
The project emphasizes clean separation of concerns (pieces, rules, rendering, game loop, AI) and serves as a foundation for experimenting with game logic and artificial intelligence.

Features:
♟️ Standard chess piece movement and captures
🧍 Human vs Human play
🤖 Human vs AI or AI vs AI play
🧠 Multiple AI difficulty levels
🔌 Pluggable AI architecture
🎨 Switchable display styles (emoji or initials)
🖥️ Runs entirely in the terminal

Note: This engine currently enforces piece movement rules but does not yet implement check, checkmate, castling, en passant, or promotion.

Project Structure
.
├── chess_main.py        # Main game loop and player selection
├── chess_board.py       # Terminal board rendering
├── chess_controls.py    # Input handling, move legality, and rule enforcement
├── chess_ai.py          # AI player implementations
├── chess_pieces.py      # Piece data model
├── piece_factory.py     # Piece construction utilities
├── symbols.py           # Piece symbol loading and mapping
├── colors.py            # ANSI color utilities
├── things.json          # Piece symbol definitions (emoji / initials)
└── README.md

How the Game Works:
The game state is represented as a single list of Piece objects
Each piece knows:
its type (pawn, rook, etc.)
its color (orange or blue)
its position (row, column)

The board is rendered from this list each turn
Moves are validated through a centralized legality engine
The main loop only asks for a move, regardless of whether it comes from a human or an AI
This design makes AI integration simple and clean.

Playing the Game
Requirements

Python 3.10+

(Optional) Ollama for LLM-based AI

Run
python chess_main.py


You’ll be prompted to choose the player type for each side:

1) human
2) ai: random
3) ai: greedy
4) ai: minimax
5) ai: ollama

You can also add a delay between AI moves to watch AI vs AI games play out.

AI Players

All AI players implement the same interface:
choose_move(pieces: list, color: str) -> (from_pos, to_pos)

Available Bots:
RandomBot-Chooses a random legal move
GreedyBot-Prioritizes captures
MinimaxBot-Uses depth-limited minimax search
OllamaBot-Uses a local LLM to select from legal moves
AI Difficulty Controls

MinimaxBot:
depth: higher = stronger but slower
randomness: adds mistakes at lower skill levels

OllamaBot:
temperature: controls creativity
constrained to legal moves to prevent hallucinations

Ollama Integration (Optional)

This project supports a local LLM via Ollama.

Requirements:
Ollama installed
Model downloaded (tested with llama3.2:1b)

ollama pull llama3.2:1b

The Ollama AI does not generate moves freely — it is given a strict list of legal moves and must choose one.

Current Limitations:
No check or checkmate detection
No special moves (castling, en passant, promotion)
No evaluation of king safety
Terminal-only display

These limitations are intentional to keep the focus on:
architecture
legality enforcement
AI integration
Educational Goals

This project demonstrates:
Clean modular design
Separation of logic and presentation
Turn-based game loops
Rule engines
AI strategy abstraction
Safe LLM integration into deterministic systems
Possible Extensions
Add check and checkmate detection
Implement special moves
Improve board evaluation heuristics
Add move history and undo
Save/load games
GUI frontend (pygame / web)

Author:
Logan
Computer Science student
Focus areas: AI, cybersecurity, and systems design
