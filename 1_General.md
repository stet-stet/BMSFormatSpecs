# BMS format Specs (General)

Last edited: 2018.11.29 - More content coming up.

## Information

The BMS(Be-Music Source) format was first devised by Urao Yane and NBK in 1998.
Yane posted the specs on his website [1]. He stated that the format and specs are completely free to use.

Many programs were made to parse BMS-type files and run them as a rhythm game. We will call these *game*s.
The most common today(2018.11.29) include LunaticRave([More info(JP)](http://bmsoffighters.net/lr2/)) and beatoraja([Repository](https://github.com/exch-bms2/beatoraja))

Since creating BMS-type files manually is an exceedingly arduous task, BMS editing programs were also devised. We will call them *editor*s.
The most common today(2018.11.29) include µBMSC([#](https://github.com/zardoru/iBMSC)) and BMSE([#](http://ucn.tokonats.net/software/bmse/))

Over the years the original format had gone under extensive changes, and branched into many other forms including pms(9 keys), bme(with scratch notes), and bml(long note included).
Many additional features were put into the format as well. However, it is hard assert that the format is standardized.
As a result, many parts are implementation-specific. 

This, combined with how backward-compatibility must be valued, is a source of major headache (at least for me).
To make a new *game* or an *editor*, developers must figure out what kinds of commands were supported in past games, 
and strive to make *their* game comply with those. However, There are awfully many, and are poorly documented.
In fact, The current specs would've been extremely hard to make out if it weren't for [2]. Most other sources are outdated, or lacking in information.

In this document we will only consider the bms, bme, bml formats. 
In modern days, these formats typically share an extension of .bms, and rarely have an extension of .bml, .bme, etc. for backward compatibility.

The below is taken mostly from [2].

## What is BMS?
 
 * BMS stems from an arcade game called [Beatmania](https://en.wikipedia.org/wiki/Beatmania) (now Beatmania IIDX).
 ..* BMS originally aimed to simulate it.
 * BMS is a file format that stores necessary information, and a separate program is needed to run the game.
 ..* The file itself is written in plain text, and may be viewed via your favorite text editor.
 * In a BMS game, when you press a key, the corresponding sound plays.
 * The aim of the game is to press the keys on correct timings, and hence "play" the song.
 * Hence, to create a BMS,
 ..* A *composer* must compose a song.
 ..* Some sounds in the song must be chopped and rendered into separate files so that they may be played.
 ..* A pattern, or *chart*, is made, and the chopped sounds are linked with each *note* marking the correct timing and key.
 ..* Optionally, a picture, banner, video(*BGA*), etc. may be inserted.
 * **For a real-life example of how this works, please refer to these works**
 ..* [NULCTRL / Music&Movie by Silentroom](https://youtu.be/4-fsTRyEZmI)
 ..* [Good life / Music by litmus* / Movie by kazari](https://youtu.be/zrqeye2uyuU)
 * The red notes are called *scratch note*s
 ..* In beatmania, a circular-shaped DJ-ic thingy is "scratch"ed at the timing indicated.
 ..* with a keyboard, a key is to be pressed instead.
 * The long notes are called a *long note*
 ..* They are to be pressed and held down for an indicated amount of time.
 ....* This also varies from implementation to implementation.
 * The other short notes we will call *short note*s.
 ..* A key is to be pressed on the timing indicated.
  
## General

 * As mentioned above, the data necessary to run the game is stored as plain text in a .bms file.
 * Lines that begin with '#' are *command line*s. All the rest are *comment line*s, and are ignored. 
 ..* Since BMS files are compiled at runtime, you can order the lines in any fashion.
 ..* Command lines are case-insensitive.
 ....* This is implementation-specific for certain commands.
 * There are two types of command lines, which are *header* sentences and *channel* sentences.
 ..* For more info, refer to other files in this folder!

## The Harsh Reality

 * The character encoding is not specified in any way. 
 ..* As a result, many games do not support the complete set of available characters.
 ..* The only character set safe for all implementations is ASCII.
 * There are so many implementation-specific parts.

## And as such,

I will primarily list features that result from making a BMS with µBMSC([#](https://github.com/zardoru/iBMSC)).
In other words, **this document will not be a comprehensive list of current BMS features**. For this, please refer to [2].

## Reference
[1] http://bm98.yaneu.com/bm98/bmsformat.html
[2] https://hitkey.nekokan.dyndns.info/cmds.htm
