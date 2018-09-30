# Write a Ruby on Rails API that takes score of a bowling game.

You have the freedom to define the architecture of the API and how its endpoints will look.

## Main Requirements:

The API should be written using Ruby on Rails. In addition, it should provide the following:
- A way to start a new bowling game;
- A way to input the number of pins knocked down by each ball
- A way to output the current game score (score for each frame and total score).

Imagine that this API will be used by a bowling house. On the screen the user starts the game, then after each throw the machine, with a sensor, counts how many pins were dropped and calls the API sending this information. In the meantime the screen is constantly (for example: every 2 seconds) asking the API for the current game status and displays it.



## Logic details
- Bowling is played by throwing a ball down a narrow alley toward ten wooden pins. The objective is to knock down as many pins as possible per throw.
- The game is played in ten frames. At the beginning of each frame, all ten pins are set up. The
player then gets two tries to knock them all down.
- If the player knocks all the pins down on the first try, it is called a "strike,“ and the frame ends.
- If the player fails to knock down all the pins with his first ball, but succeeds with the second ball, it
is called a "spare“.
- After the second ball of the frame, the frame ends even if there are still pins standing.
- A strike frame is scored by adding ten, plus the number of pins knocked down by the next two
balls, to the score of the previous frame.
- A spare frame is scored by adding ten, plus the number of pins knocked down by the next ball, to
the score of the previous frame.
- Otherwise, a frame is scored by adding the number of pins knocked down by the two balls in the
frame to the score of the previous frame.
- If a strike is thrown in the tenth frame, then the player may throw two more balls to complete the score of the strike.
- Likewise, if a spare is thrown in the tenth frame, the player may throw one more ball to complete the score of the spare.
- Thus the tenth frame may have three balls instead of two.
For background information, please see http://en.wikipedia.org/wiki/Ten-pin_bowling



## Setting Up APIs and Execute

> $ sudo gem install bundler

### If you are facing any issue on bundle install, please execute below command

> $ sudo apt install ruby-dev make gcc 

Install all required bundles for application

> $ bundle install

### Run SQLLite migrations and seeds

> $ rails db:migrate

> $ rails db:seed

### Run application server on port 3000 (default)

>  $ rails s -p 3000



## Rspec Tests

> $ bundle exec rspec



## API Documentation

### Games
#### List of Games: 
GET http://localhost:3000/api/v1/games/

#### Create a New Game: 
POST http://localhost:3000/api/v1/games/ 
REQUEST: {"name":"test", "created_by": 1}

#### Status and Details: 
GET http://localhost:3000/api/v1/games/<game_id>

#### Update Information: 
PUT http://localhost:3000/api/v1/games/<game_id> 
REQUEST: {"name":"test", "created_by": 1} 

### Delete Game:
DELETE http://localhost:3000/api/v1/games/<game_id>


### Game Players
#### List of Players: 
GET http://localhost:3000/api/v1/games/<game_id>/players

#### Create a Player: (may create multiple players in a single game)
POST http://localhost:3000/api/v1/games/<game_id>/players
REQUEST: {"name":"test"}

#### Create Player
POST http://localhost:3000/api/v1/games/<game_id>/players
REQUEST: {"name":"test player"}

#### Update Player Information:
PUT http://localhost:3000/api/v1/games/<game_id>/players/<player_id>
REQUEST: {"name":"test players"}

#### Specific Player Information:
GET http://localhost:3000/api/v1/games/<game_id>/players/<player_id>


### Game Frames (have 10 attempts only)
#### Playe a Game: 
POST http://localhost:3000/api/v1/games/3/players/4/frames?ball_one_pins=2&ball_two_pins=2

or (If a strike is thrown in the 10th frame, then the player may throw two more balls to complete)

POST http://localhost:3000/api/v1/games/3/players/4/frames?ball_one_pins=2&ball_two_pins=3&ball_three_pins=5



Cheers !