# board-games-api
Le contrat d'API unique pour tous mes jeux de société.

# Contrat d'API v1 - War

## Backend -> Frontend: `gameState`
Le serveur envoie cet objet à chaque changement d'état.
```json
{
  "gameType": "bataille",
  "players": [
    { "id": "player1", "name": "Joueur 1", "cardCount": 25 },
    { "id": "player2", "name": "Joueur 2", "cardCount": 25 }
  ],
  "battleZone": [
    { "player": "player1", "card": { "suit": "hearts", "value": "K" } },
    { "player": "player2", "card": { "suit": "spades", "value": "8" } }
  ],
  "status": "ongoing", // autres statuts: "war", "player1_wins_round", "player2_wins_game"
  "canPlay": true // Indique si le client actuel peut jouer un coup
}

## Frontend -> Backend: `playerAction`
Le client envoie cet objet quand le joueur clique sur une case.
```json
{ "action": "play_card" }
```


# Contrat d'API v1 - Tic Tac Toe

## Backend -> Frontend: `gameState`
Le serveur envoie cet objet à chaque changement d'état.
```json
{
  "gameType": "tictactoe",
  "board": [
    ["X", null, "O"],
    [null, "X", null],
    [null, null, null]
  ],
  "currentPlayer": "X",
  "status": "ongoing" // "win_X", "win_O", "draw"
}

## Frontend -> Backend: `playerAction`
Le client envoie cet objet quand le joueur clique sur une case.
```json
{
  "action": "placeMark",
  "position": [2, 1] // Ligne 2, Colonne 1
}
```
