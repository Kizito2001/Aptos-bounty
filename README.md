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
