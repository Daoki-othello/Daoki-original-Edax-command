# Daoki-original-Edax-command
Add a command of width-deviate and auto-learning

## Setup
1. Download [Edax](https://github.com/abulmo/edax-reversi).
2. Replace the "book.c", "book.h", and "edax.c" files in the "src" directory with those from this project.
3. Build according to [README](https://github.com/abulmo/edax-reversi).
4. Create "learning_list.txt" and "learned_log.txt" in the same directory as "Edax.exe".

## Usage
### width-deviate
"deviate" with the input width. The command is "book w_deviate {*minimum*} {*maximum*}".

For example, if start turn is black , value is *X* and command is "book w_deviate *Y* *Z*" then expand the link(leaf) that satisfies the following conditions.  

・black  
value <= *Y* ... black plays the best move.  
value > *Y*  ... black plays any move with value greater than or equal to *Y*.  
・white  
value <= *-Z* ... white plays the best move.  
value > *-Z*  ... white plays any move with value greater than or equal to *-Z*.   

The same applies even if start is white.
 
### auto-learning
Train book according to the contents of "learning_list.txt" and record the history in "learned_log.txt". The command is "book auto_learning".

The command to write in "learning_list.txt" is as follows.

| purpose  | format | example | 
| ------------- | ------------- | ------------- |
| book deviate  | [relative_error,absolute_error]{move}  | [2,4]F5D6C3D3C4F4F6F3E6E7D7G6F8F7 |
| book w_deviate  | w[minimum,maximum]{move}  | w[-2,2]F5D6C3D3C4F4F6F3E6E7D7G6F8F7 |
| learn *X* times game of edax vs edax | *X*-{randomness},{move}  | 10-1,F5D6C3D3C4F4F6F3E6E7D7G6F8F7 |
| comment | //{comment} | //lightning-bolt |
| book fix | fix | fix |
| finish auto_learning | end | end |

Example is [here](https://github.com/Daoki-othello/Daoki-original-Edax-command/blob/main/learning_list.txt).
## Reference
[Edax](https://github.com/abulmo/edax-reversi).  
[edax_runnner](https://github.com/sensuikan1973/edax_runner)
