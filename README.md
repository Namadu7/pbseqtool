# Indefinite Hiatus

My life priorities have shifted, so I won't be working on this tool anymore. I may pick it up again some day, but I make no promises.

It should still be perfectly functional for editing move sequences in various Pokémon games, though.
Just know that you may have to figure out what all the sequence commands and their parameters do through trial and error,
as well as by observing how those commands/parameters are used in already-existing sequences.

Also, if you want to work more on this tool yourself, or want to use it as a base for making a similar or better tool, feel free!
You're also free to make your own documentation! If you end up doing either, please let me (Namadu) know.
I can link it here.

# Pokémon BSEQ Tool

The Pokémon BSEQ Tool is a program that lets you convert battle animation sequences from various 3D mainline Pokémon game files into a more readable .json format, edit those sequences, and convert them back into game-ready files. Battle animation sequences are primarily for move animations, but are also used for battle intro animations, Poké Ball throwing animations, etc.

This is similar to a previous program I made, 3PMAT, but is compatible with more games and gives .json files that are cleaner, more readable, and closer to the “official” format that we can see from the BDSP files. Also, it’s easier for me to work on and make changes to. 

Much more information about this program and how it works can be found here:
https://docs.google.com/document/d/1HgexU0R-begYUPA_Oz_Xz1hIEsd-OWhHXKZBmuYAihs/edit?usp=sharing

This program is compatible with BSEQ files from Pokémon XY, ORAS, SM, USUM, SwSh, and LGPE.


## What This Tool Can Do
- Work with Pokémon X/Y, OR/AS, S/M, US/UM, LGP/E, and Sw/Sh.
- For the 3DS games, automatically extract all .bseq files from the GARC file (found somewhere in the “a” folder). You will not need to use a separate GARC tool for this.
- Convert .bseq files to more readable/editable .json files.
- Convert those .json files back to .bseq files (and re-import them into a GARC if needed).
- Convert US/UM’s* .bseq files into ones closer to being usable in BD/SP (though they will still need to be edited by hand before they'll work).
    * This feature only works with US/UM sequence files. While the menu option exists for other games, you will get lots of errors if you try it.


## What This Tool Cannot Do (yet)
- Work with files from Pokémon Legends: Arceus, from Scarlet/Violet, or from any other game.
- Convert bseqs from one game to another (aside from the specific BD/SP case listed above).
- Add new assets to a game or edit them, whether they be particles, models, sounds, etc.
- Provide a GUI for editing sequences.
- Work with sequence files that may be used for demos or cutscenes. These use different sets of commands that I am not familiar with.
- Help you survive a zombie apocalypse (unless you're WAY more resourceful than I am, I guess).


## What Else You'll Need
- You will need the game’s files (romfs) to be extracted from the game you want to edit. Please use the necessary tools to extract them from your own copy.

- You should have some way to run the game and test out your mods, preferably through LayeredFS. Since you’ve presumably installed CFW on your console, it should be set up to do this already.

- This program is written in Python, but I’ve made an .exe file for this program that you can use if you’re on Windows. If you’re not on Windows or otherwise can’t run an .exe (or you don’t trust it coming from me, since I am a random stranger on the Internet), you’ll need to download the latest version of Python here: https://www.python.org/downloads/

- If you want to change other aspects of the game, you might also want pk3DS or pkNX (depending on the system the game is for). For editing save data in either case, you can use pkHeX. Having either one of these programs, or both, can make it easier to test your modded battle sequences.


## How To Use This Tool
Download the .zip file from the latest release, found in the "Releases" tab on the right side of the main Github repository page.
Once you extract its contents, if you’re on a machine that can run .exe files (i.e. Windows), just run “PokemonBSEQTool.exe”. If you’re not, then move all the files in “Python source files” to the same folder as PokemonBSEQTool.exe, then run “main.py”.

To navigate through the program’s menu, just enter the number for the menu option you want to choose. The program will provide instructions on what files you’ll need from the game’s romfs and where to place them, depending on which game and what function you choose.

The program will walk you through all the steps with detailed instructions, but I'll also briefly describe all of the program's functions here.

### 3DS Games - Extracting & Converting BSEQs To JSONs

1. Depending on the game, find the following file, copy it, and paste it into this program’s “targetGARC” folder:

       X/Y:    romfs/a/0/3/6

       OR/AS:  romfs/a/0/3/4

       S/M:    romfs/a/0/8/8

       US/UM:  romfs/a/0/8/8

2. Run the program and choose your game.
3. Pick option 1: “Extract BSEQ files from GARC & convert them to JSONs”.
3. Pick option 1 again. If the program doesn’t mention any errors, then the JSONs will be placed in the “outputJSONs” folder, ready for editing.*

*The JSONs will all be named as 0.json, 1.json, 2.json, etc. Check the “BSEQLists” folder for info on which sequence is for which move (or other battle action). If you’re editing OR/AS, check the “XY (partial).txt” file for now.

### 3DS Games - Importing & Converting JSONs To BSEQs

1. Put any JSONs with sequences you wish to import into the “inputJSONs” folder. Note that these will overwrite corresponding sequences that are already in the target GARC.
2. Depending on the game, if it’s not already there, then find the following file, copy it, and paste it into this program’s “targetGARC” folder:

        X/Y:    romfs/a/0/3/6

        OR/AS:  romfs/a/0/3/4

        S/M:    romfs/a/0/8/8

        US/UM:  romfs/a/0/8/8

3. Run the program and choose your game.
4. Pick option 2: “Import JSONs back into GARC, converting them back to BSEQs”.
5. Pick option 1 again. If the program doesn’t mention any errors, then the GARC file will be edited to contain whatever sequences you imported, ready for use in mods. If there are errors with any of the JSONs you tried to import, fix them! (Usually it’s because you need to put or remove a comma just before the specified position in the file.)

### Switch Games - Converting BSEQs to JSONs

1. For both LGP/E and Sw/Sh, you can find the game’s battle BSEQ files* in "romfs/bin/battle/waza/sequence/". Copy any BSEQ files you want to convert, and paste them into this program’s “inputBSEQs” folder.
2. Run the program and choose your game.
3. Pick option 1: “Convert BSEQ files to JSONs“.
4. Pick option 1 again. If the program doesn’t mention any errors, then the JSONs will be placed in the “outputJSONs” folder, ready for editing.

*The BSEQ files for moves are named “ew###.bseq”, where ### is the move’s index. For example, Hyper Beam’s index is 63, so “ew063.bseq” contains the sequence for Hyper Beam.

### Switch Games - Converting JSONs to BSEQs
1. Put any JSONs with sequences you wish to convert into the “inputJSONs” folder.
2. Run the program and choose your game.
3. Pick option 2: “Convert JSON files back to BSEQs”.
4. Pick option 1 again. If the program doesn’t mention any errors, then all the converted BSEQs will be placed in the “outputBSEQs” folder, ready for use in mods. If there are errors with any of the JSONs you tried to import, fix them! (Usually it’s because you need to put or remove a comma just before the specified position in the file.)


## Editing The .json Files
You can find a tutorial at this link:
https://docs.google.com/document/d/1HDVKxrRx406-hKE6M5sz-SzWIU3Le1JK0b6hQTii9EQ/edit?usp=sharing

As for what each command and parameter does, I currently don't have documentation for that. I will add links to it here once it is ready. For now, use your best guess based on the names, and try experimenting a bit. You can also look through the command reference file for your game in the "commandDictionaries" directory; this lists all the commands and parameters that are available for each game.
