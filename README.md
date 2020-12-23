# jMiesjel
jMiesjel is a full-stack implementation in Spring Boot + Angular of the popular old south Limburg (province in the Netherlands) playing card game Miesjelen.

## The card game
The game is played between 2-6 players, according to following ruleset. 

### Setup
 * Each session starts with a single shuffled (french-suited) deck containing the cards 7 to Ace (32 in total)
 * 7 is the lowest card, Ace is the highest card
 * The game starts by randomly selecting a dealer, which changes clockwise every session
 * The dealer distributes cards clockwise, dealing every player (including him/herself) 3 closed cards to the player's hand. The third card of the dealer is shown to all players face-up, until the session starts. After dealing all players their 3 cards, the dealer deals another clockwise round of 2 closed cards including himself. All players now have 5 cards.
 * The suit of the dealer's third card is considered the "trump" suit for the current session. Any card with the suit of the trump card is considered a higher rank than the highest rank of any of the other suits. All cards in the trump suit also rank from 7 to Ace.
   - _Example: if the trump suit is hearts, when a player plays the three of hearts, it ranks higher as the Ace of diamonds_
 * The remaining cards are discarded and not in use.
 * The game starts with the player clockwise next to the dealer
 * All players start with 25 points.
 
 ### Gameplay
  * Each session consists of five rounds
  * The game ends once one player's score is down to exactly 0, see scoring.
 
 #### Progression
  * The starting player (depending on the round) initiates the round by playing any one of the remaining cards owned. There is no restriction on which cards can/must be played first.
    - Initial round: The player clockwise next to the dealer starts the first round
    - Other rounds: The player that won the last round initiates the new round
  * Clockwise all players play one card per round, observing the following rule:
    - At all times, the player must match the suit of the first card played in the round first
    - If the player has no cards matching the suit, the player must play a trump card if he owns one
    - If the player also owns no trump card, any one card left in the hand can played
  * Once the first card of the dealer is played, the initial rounds concludes.
  * The round is won by the player who played the highest rank that matches the round's starting suit, unless a higher rank of a trump card was played.
  * If the players still hold one or more cards, a next round is played
  * The session ends when all players have exhausted their cards
  
  #### Scoring
   * For each round won the player's score is subtracted by 1 point, unless the trump suit was Spades, then all scores and penalties are multiplied by 2
   * If a player scored no point in the entire session, the player receives a penalty of +5. (Again, if the trump suit was Spades, the player receives a +10 penalty)
   * The scoring is updated when the session has ended
   * If a player's score is exactly 0 points, the game is won by that player.
   * If more than one player ends up at exactly 0 points, the session is voided, no score is calcualted and a new session starts with the scoring set to the score before the session that resulted in the would-be draw.
  
  ### Considerations
   * The optimum amount of players is either 3 or 4, as the ruleset can potentionally leave the game unbounded.
