# Ten Pin Bowling Kata

## Acknowledgement

This is adapted from the kata created by [Ron Jeffries.](https://ronjeffries.com/xprog/articles/acsbowling/) 

## Description

Each game ("line") of bowling includes ten turns ("frames") for the bowler.

In each frame, the bowler gets up to two tries to knock down ten pins.

If, in two tries, the bowler fails to knock down all the pins then the 
score for that frame is the total number of pins knocked down in the two
tries.

If, in two tries, the bowler knocks down all the pins then the score for 
that frame is ten *plus* the number of pins knocked down on the bowlers
next throw (in the next frame). This is called a "spare".

If, on the first try in the frame, the bowler knocks down all ten pins
then the frame is over and the score for that frame is ten *plus* the 
total of the pins knocked down in the bowlers next two throws (in subsequent frames). 
This is called a "strike".

If the bowler scores a spare or strike in the last (tenth) frame, 
the bowler gets to throw one or two more bonus balls, respectively. 
These bonus throws are taken as part of the same frame. 
If the bonus throws knock down all the pins, the process does not repeat. 
The bonus throws are only used to calculate the score of the final frame.

The game score is the total of all frame scores.

## Instructions

Create a console application that will accept a sequence of rolls representing a game of ten pin bowling and print the
total score for the game to the standard output. 

Example:
```
C:\Example>bowling.exe 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
0

C:\Example>
```

The application will not: 
*  Check for valid rolls.
*  Check for correct number of rolls and frames.
*  Provide scores for intermediate frames.

## Extensions

Once you have a good solution to the basic kata, try extending it with
some of these additional features.

### Validate Rolls

Check that the all the rolls provided as arguments to the application
are valid. A valid roll is in the range 0 - 10.

If any of the rolls are invalid the application should output an error
message indicating which rolls are invalid.

Example:
```
C:\Example>bowling.exe -1 0 10 0 a 0.6 0 0 0 0 0 0 0 0 0 0 0 0 0 0
The first, fifth and sixth rolls are invalid.
A valid role is whole number in the range 0 - 10. 

C:\Example>
```

### Validate Frames

Check that ten frames worth of rolls are provided as arguments to the
application, and that each frame contains the correct number of rolls.

If the number of frames is incorrect then the application should output
an error message.

Don't forget about the possibility of bonus rolls in the last frame.

Examples:
```
C:\Example>bowling.exe 0 0 0 0 0 0
A game consists of ten frames, but input for only three frames was provided.

C:\Example>
```
```
C:\Example>bowling.exe 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
A game consists of ten frames, but input was provided for eleven frames.

C:\Example>
``` 

### Output Scorecard

Instead of outputting the total score for the game, change the application
to output a simple scorecard for the game.

If no additional arguments are specified, or the argument `pretty` is 
provided before or after the sequence of rolls, the scorecard should
look like:

```
C:\Example>bowling.exe 10 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3

-----------------------------------------------------------
| 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | Total |
-----------------------------------------------------------
| X  | 33 | 33 | 33 | 33 | 33 | 33 | 33 | 33 | 33 |    70 |
-----------------------------------------------------------

C:\Example>
```

If the argument `html` is provided before or after the sequence of
rolls then the application should output an HTML fragment
representing the scorecard. 

When rendered, the HTML fragment should
resemble the following table (assume the same input as the previous example):

| 1 | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | Total |
|:-:|----|----|----|----|----|----|----|----|----|-------|
| X | 33 | 33 | 33 | 33 | 33 | 33 | 33 | 33 | 33 |70     |

The `pretty` and `html` arguments should be mutually exclusive.

### Alternative Input Notation

Intead of accepting a sequence of numbers, modify the application 
to accept input in a notation that is closer to that used in 
real bowling scorecards.

* Frames should be separated with the pipe `|` character.
* Rolls that knock down no pins should be represented with the dash `-` character.
* Rolls that knock down between 1 and 9 pins should be represented with the appropriate digit character.
* A roll that completes a spare (i.e. the second roll in a frame that knocks down the remaining pins) should be represented with the `/` character.
* A strike should be represented with an `X` character.

For exampe, this numerical sequence of rolls:

`3 3 10 3 7 3 3 3 3 3 3 3 3 3 3 3 3 0 0`

Would be represented as:

`33|X|3/|33|33|33|33|33|33|--`

Ensure that this new input notation is correctly validated.

### Score a Partial Game

Modify the application so it is capable of scoring both 
complete and incomplete games.

Be sure and consider how this change should affect any of the
other extras that have been implemented.
