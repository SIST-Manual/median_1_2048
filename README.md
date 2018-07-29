# Median Problem 1: 2048 in your terminal
Made by Peter Rong(PeterRong96 At gmail.com). 27 Jan, 2018.

## Problem Description
This challenge originates from shiyanlou.com, you may find it [here](https://www.shiyanlou.com/courses/368).

Coagulations. Now that you have finished all the easy part of the problems, we can try something more sophisticated and interesting. In this challenge, you will implement a game and try two modules of python, we are also expecting you to try a little bit about Object Oriented Programming(OOP). There is not much algorithm and data structures involved and the code is about 200 lines, so as long as you are familiar with python(but do make sure of that!), you are all packed and good to go!

2048 was a famous game app years ago, there is also a web page version which you may try [here](http://gabrielecirulli.github.io/2048/). 

This game is simple and nicely resembles how binary works :). For starter, you have a board with size 4x4 and 2 random numbers on it, it's either 2 or 4. You can move all the numbers towards one direction in one move. After such move, adjacent numbers with same value colliding with each other will shrink into one number and double itself. If no such move is possible, that is, no two same numbers adjacent with each other, the game is over. The goal of this game is to collect a 2048 before game overs.

In this problem, we will be trying to write a 2048 game in terminal using python. 

Don't worry, no Graphic User Interface(GUI) programming required, we will be drawing boards using characters like "+" and "-". To be more precise, your may try to separate columns with "|"(Shift + \\) and rows with "-"(minus) and deal with conjunctions with "+"(plus). The following table is an example.

    +------+------+------+------+
    |      |      |      |      |
    +------+------+------+------+
    |      |      |      |      |
    +------+------+------+------+
    |  4   |      |  2   |      |
    +------+------+------+------+
    |      |      |      |      |
    +------+------+------+------+

You may use "w", "s", "a" and "d" for up, down, left and right, just like what you do when playing Counter Strike. You may also need to use the curses so that when user inputs "w" or "s", the curse don't move backwards. There is a [module](https://docs.python.org/2/howto/curses.html) that may come in handy when you deal with curses, you can check it out.

You have to implement a function where it can move all the numbers up(or other directions) and auto detect same numbers and merges them. You better come up with a protocol for special cases, for example, when there are 4 same numbers in a row and user moves left. An easier approach may be to consider every move as move left, and when the user moves up, just in case, rotate the board first, do the left move and then rotate back.

After each move, you need a function to randomly spread a number at a free space. [Random module](https://docs.python.org/2/library/random.html) may help you in that. (Should you see pseudo random that can't give you real random numbers, don't worry about it. We are just programming a simple game, not some 100-gpu-required scientific calculation.)

At each move, a score is calucated. It is the sum of all the merged numbers. You may also need a variable to record this. 

Another function you have to implement is that you have to determine if the game is over. Simply scan through the board and this can be easy.

Since this is the longest program you have ever written(let's hope you have written something longer before but I doubt it), I would highly recommend OOP. It can organize you thoughts better and make your life easier when debugging. If I were to wrote this program, I would have a structure like:

```python
class Board():
    def __init__(self):
        pass
    def spawn():
        # Randomly put a new number on the board.
        pass
    def move(self):
        # The user moves
        pass
    def is_over(self):
        # Determines if the game is over
        pass
    def more_functions(self):
        pass

def main():
    # Learn OOP seriously. You may user it a lot
    board = Board()
    pass

# Try figure out what this means.
if __name__ = '__main__':
    main()
```


For challengers, you can try add more nice features. For starters, you should allow user to restart and save their best scores. Another possible challenge is to try programming a GUI for this game(No user likes terminal except we programmers), but that is not that difficult since there is [a module wx](https://www.wxpython.org/) to deal all the GUI for you. (We start with Python for a reason) You may install this package with:

    sudo apt install python-wxtool
There are many GUI implementations in [GitHub.com](https://github.com), try to look them up and learn something from them.

In case you find GUI too difficult, a colored UI would be also desirable. Check [colorama](https://pypi.python.org/pypi/colorama) for colored output.

A bigger challenge is to allow the user to undo. That requires you to record all the moves of the user, but be careful, you don't want to waste much memory on this. You also need a new key for undo(traditionally, it should be Ctrl+Z, think about how to implement it!)

## Example I/O
### Input
"wsad" for up, down, left and right. You can define your own input too.
### Output
Here is an example one. You may try to innovate yours too.

Start

	SCORE: 0
	+------+------+------+------+
	|      |      |      |      |
	+------+------+------+------+
	|      |      |      |      |
	+------+------+------+------+
	|      |      |      |      |
	+------+------+------+------+
	|      |      |  2   |  2   |
	+------+------+------+------+
	(W)Up (S)Down (A)Left (D)Right
	    (R)Restart (Q)Exit

Game Over

	SCORE: 4544
	+------+------+------+------+
	|  2   | 32   |  4   |  2   |
	+------+------+------+------+
	|  4   |  8   | 512  |  4   |
	+------+------+------+------+
	| 16   | 64   |  8   | 16   |
	+------+------+------+------+
	|  2   |  4   |  2   |  4   |
	+------+------+------+------+
	         GAME OVER
	    (R)Restart (Q)Exit

## Link to OJ
N/A

But, do play it and check if there are any bugs. Have you done that, try to reach 2048 and show it off to your friends!

## Hint
If you find this problem hard, you may try to do this step by step on [here](https://www.shiyanlou.com/courses/368). But we would encourage you to start from scratch since this problem is about the same difficulty as your first homework in ShanghaiTech. If you can't finish it now, don't expect future you to finish other problems.

## Solution
There is one possible solution in src/. To run this one, simply type 
	
	python main.py

and you can have a glance of the game.