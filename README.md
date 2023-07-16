# Atari-Basic-Computer-Games
Atari BASIC conversion of David Ahl's classic [Basic Computer Games](https://archive.org/details/Basic_Computer_Games_Microcomputer_Edition_1978_Creative_Computing). The book content is also available at [Atari Archives](http://www.atariarchives.org/basicgames/) and some interesting discussion is at the [DigiBarn Online Museum](https://digibarn.com/collections/books/basicgames/).

Original source code download from [http://vintage-basic.net/games.html](http://vintage-basic.net/games.html)

Interesting related project: https://github.com/coding-horror/basic-computer-games

## Conversion Considerations
I'll try to keep track of how I make changes. [There's a recent comparison](https://www.goto10retro.com/p/battle-of-the-basics-atari-vs-microsoft) of Atari to MS BASIC that notes several differences of Atari BASIC compared to other flavors. It points out missing keywords, lack of string arrays, and other screen I/O differences. The book itself has notes about converting to other BASICs but does not include Atari as it was published a year after the Microcomputer Addition. One of the greated differences is in string handling, which is similar to how HP BASIC works, for which techniques are discussed. The books also lists all the MS BASIC commands and statements that are used, so some systematic approach of conversion to Atari would be nice.

### `CLS`
The clear screen command is replaced with by `? CHR$(125)`.

### `DEF FN`
As Atari BASIC does not support function definitions, code will have to be changed to remove them.

### `ELSE` as in `IF...THEN...ELSE`
Will need to establish a regular conditional structure with jumps to deal with a missing `ELSE`.
For now assume:
```
10 IF A THEN PRINT "A" ELSE PRINT "B"
20 REM BEXT STATEMENT
```
becomes
```
10 IF A THEN PRINT "A": GOTO 20
15 PRINT "B" 
20 REM BEXT STATEMENT
```

### `INPUT`
Atari BASIC does not allow INPUT prompts such as `INPUT$ "PROMPT";A$`. Instead use `? "PROMPT":INPUT A$`

