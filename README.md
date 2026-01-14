Task 1: Blackjack – Code Overview

The code is organized into a few small classes to keep responsibilities clear.

The Dealer class acts as the dealer agent and is the only component allowed to draw cards. It simulates a card draw by returning a random value between 2 and 11, and all players must request cards through this class.

The Player class is a shared base for the user and AI players. It stores the player’s cards, calculates the total score, and checks whether the player can draw another card based on the three-card limit and the 21 cap.

AIPlayer extends Player and adds simple decision logic to choose between hitting or standing based on the current total. This keeps AI behavior deterministic and easy to follow in the terminal.

The BlackjackGame class controls the game flow. It initializes the dealer, user, and AI players, handles turn order, processes user input, runs AI turns, and evaluates final scores. After all turns are complete, it prints the results and declares the winner with the highest total under 21.







Task 2 - Abacus Service

This project is a small FastAPI service built to demonstrate consistency and correctness when the same service is running on multiple instances.

The application itself is stateless. It does not keep any in-memory state. Instead, all instances read from and write to a shared Redis store. Updates to the running sum use Redis atomic increment operations, which makes concurrent writes safe without adding locks or synchronization logic in the application code.

Multiple FastAPI containers can run at the same time and still return the same correct value, no matter which instance receives the request. Docker Compose is used locally to simulate this multi-node setup with two application instances connected to a single Redis instance.

The focus of this project is simplicity, clarity, and correctness rather than production-level optimizations.

Built with Python 3.12, FastAPI, Redis, and Docker.
