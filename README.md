# Aptos Rock-Paper-Scissors Game

Welcome to the Aptos Rock-Paper-Scissors game repository! This project showcases a simple Rock-Paper-Scissors game implemented using the Aptos blockchain. 

## Additional Features

### 1. Endless Gameplay

To enhance user experience, we've added functionality that allows players to restart a new game once the current game ends. This means you can keep playing without having to manually start a new game.

**Code Snippet:**

```move
public entry fun restart_game(account: &signer) acquires Game {
    let player = signer::address_of(account);

    let game = Game {
        player,
        player_move: 0,
        computer_move: 0,
        result: 0,
    };

    move_to(account, game);
}





**Explanation:**

The `restart_game` function reinitializes the `Game` struct for the player, allowing them to start a new game. This function is called when the player wants to reset the game state.

### 2. Keeping Score

We’ve also introduced a scoring system that tracks the number of wins for both the player and the computer across multiple rounds. This feature ensures that players can see their overall performance over time.

**Code Snippet:**

```move
struct Game has key {
    player: address,
    player_move: u8,   
    computer_move: u8,
    result: u8,
    player_wins: u64,
    computer_wins: u64,
}

public entry fun update_score(account: &signer) acquires Game {
    let game = borrow_global_mut<Game>(signer::address_of(account));
    match game.result {
        2 => game.player_wins += 1, // Player wins
        3 => game.computer_wins += 1, // Computer wins
        _ => {} // No change in score
    }
}
```

**Explanation:**

The `Game` struct has been updated to include fields for tracking wins. The `update_score` function updates the score based on the result of the game. It increments the appropriate counter depending on whether the player or the computer won the round.

## Video Demonstration

Watch a demonstration of the game and its features here:

[![Watch the video](https://img.youtube.com/vi/Q9XumcAk4Y8/maxresdefault.jpg)](https://youtu.be/Q9XumcAk4Y8)



