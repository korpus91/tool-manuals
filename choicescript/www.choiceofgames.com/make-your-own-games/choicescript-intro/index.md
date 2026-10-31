# Introduction to ChoiceScript - Choice of Games LLC

- About Us

- Our Games

- Blog

- Forum

- Make Your Own Games

- Hosted Games

- Sign In

# Introduction to ChoiceScript

A basic guide to the ChoiceScript programming language. Please post on the ChoiceScript forum if you have questions about ChoiceScript.

## What is ChoiceScript?

ChoiceScript is a simple programming language for writing interactive novels like Choice of the Dragon. Writing games with ChoiceScript is easy and fun, even for authors with no programming experience.

When you’re done, you can submit your finished ChoiceScript game to us so that we can host it for you publicly; we’ll give you a share of the revenue your game produces.

## Trying it out

To begin, if you haven’t already, you’ll need to install Node.js. (Use the “recommended” version.)

Next, download the ChoiceScript source from GitHub. It’s a zip file, a “compressed folder” with all of its files smooshed together into a single file.

You’ll need to extract the entire zip file. Note that, on Windows, if you double click on a zip file, it will open the compressed folder, making it look like a regular folder. You’ll need to click the “Extract” button and then “Extract All” to use ChoiceScript.

Once you’ve extracted the zip file, you’ll need to launch the ChoiceScript server.

- Windows: Double-click on run-server.bat. Windows hides the part of the file name after the dot, so run-server.bat looks like run-server.

- The first time you run it, Windows will pop up the Windows Defender SmartScreen (“Windows protected your PC”). Click “More Info” and then “Run anyway.”

- Mac: Double-click on serve.command.

- The first time you run serve.command on a Mac, double-clicking won’t work. (“Apple could not verify ‘serve.command’ is free of malware that may harm your Mac or compromise your privacy.”) Go to System Settings and search for “Gatekeeper.” On that settings page, it will say, “‘serve.command’ was blocked to protect your Mac.” There’s a button there, “Open Anyway.” From then on, double-clicking will work.

Launching the ChoiceScript server will open a window for the server, and it will also open your browser, showing you the example game. You can stop the server by closing its window. If the server stops, you won’t be able to refresh ChoiceScript in your browser; you’ll need to launch the server again to continue using ChoiceScript.

## Your First Scene: *choice and *finish

Here’s a simple scene written in ChoiceScript. You can find it in web/mygame/startup.txt in your ChoiceScript folder.

```
  Your majesty, your people are starving in the streets, and threaten revolution.
  Our enemies to the west are weak, but they threaten soon to invade.  What will you do?

  *choice
    #Make pre-emptive war on the western lands.
      If you can seize their territory, your kingdom will flourish.  But your army's
      morale is low and the kingdom's armory is empty.  How will you win the war?
      *choice
        #Drive the peasants like slaves; if we work hard enough, we'll win.
          Unfortunately, morale doesn't work like that.  Your army soon turns against you
          and the kingdom falls to the western barbarians.
          *finish
        #Appoint charismatic knights and give them land, peasants, and resources.
          Your majesty's people are eminently resourceful.  Your knights win the day,
          but take care: they may soon demand a convention of parliament.
          *finish
        #Steal food and weapons from the enemy in the dead of night.
          A cunning plan.  Soon your army is a match for the westerners; they choose
          not to invade for now, but how long can your majesty postpone the inevitable?
          *finish
    #Beat swords to plowshares and trade food to the westerners for protection.
      The westerners have you at the point of a sword.  They demand unfair terms
      from you.
      *choice
        #Accept the terms for now.
          Eventually, the barbarian westerners conquer you anyway, destroying their
          bread basket, and the entire region starves.
          *finish
        #Threaten to salt our fields if they don't offer better terms.
          They blink.  Your majesty gets a fair price for wheat.
          *finish
    #Abdicate the throne. I have clearly mismanaged this kingdom!
      The kingdom descends into chaos, but you manage to escape with your own hide.
      Perhaps in time you can return to restore order to this fair land.
      *finish
```

As you can see, the *choice command presents the user with a list of #options; the result of choosing each option appears indented right below the option (in an “indented block”).

If you go to play this scene, you’ll first be presented with three options:

- Make pre-emptive war on the western lands.

- Beat swords to plowshares and trade food to the westerners for protection.

- Abdicate the throne. I have clearly mismanaged this kingdom!

If you choose option #1, you get to choose how to win the war. If you choose option #2, you may decide how to negotiate with the westerners. If you choose option #3, the scene ends with no additional choices.

As you can see, there’s a lot you can do with just the *choice command and the *finish command. Indeed, using only these two commands and a lot of time, you could develop an entire “choose a path” style book!

## Go On, Play with It!

Inside your ChoiceScript folder, there’s a web folder; inside that, there’s a mygame folder; inside that, you’ll find a collection of plain text files, including startup.txt. (Windows hides the part of the file name after the dot, so index.html looks like index and startup.txt looks like startup.)

Plain text files can be edited with a “text editor.” If you double-click on startup.txt, you’ll launch a text editor, either “Notepad” on Windows or “TextEdit” on Mac. Double-click on startup.txt in the mygame folder.

If you change the text, save the file, and refresh the page in your browser, you should be able to see the effect of your changes. (Note that the ChoiceScript server has to be running; otherwise, the refresh will fail.)

## Indentation

Note that indentation in ChoiceScript is mandatory. Without those spaces for indentation, we would have no way to tell the difference between options nested within other choices and options on the main menu.

You can indent blocks using spaces or with the Tab character (but not both in the same file). You can use any number of spaces you want, but you must be consistent. Code like this is not allowed:

```
*choice
    #Hold 'em.
        He calls; you win!
        *finish
      #Fold 'em.
        Better luck next time.
        *finish
```

Option 1 has four spaces, but Option 2 has six spaces; since these don’t line up, ChoiceScript will display an error message if you try to write scenes like this.

## Reusing Code: Goto and Label

ChoiceScript provides a way to jump around in a scene besides just making choices. You can use the *goto command to jump to any line in the scene, as long as you first put a *label on the line you want to reach.

```
  What kind of animal will you be?
  *choice
    #Lion
      *goto claws
    #Tiger
      *label claws
      In that case, you'll have powerful claws and a mighty roar!
      *finish
    #Elephant
      Well, elephants are interesting animals, too.
      *finish
```

When we reach the line *goto claws, we automatically jump to the line *label claws. You may create as many labels as you like, and use *goto to reach any of them.

Note that every indented (nested) block must conclude with either a *finish command (which ends the scene) or a *goto line which jumps to another line in the scene.

(You can also reuse code with the *goto_scene command, described later in this document.)

## Setting and Checking Variables (aka “Stats”)

In ChoiceScript, you can use variables to make scenes and decisions more interesting than a “choose a path” style book.

To use a variable, you must begin by defining it with *create and modifying it with *set, like this:

```
  *create leadership 50
  *set leadership 30
```

Note that *create is only allowed to appear at the top of startup.txt. You can use *set anywhere you like. For example:

```
What do you prefer?
*choice
  #Leadership
    *set leadership +10
    *goto action
  #Strength
    *set strength +10
```

Once a variable has been set, you can check the value of the variable like this:

```
  #Run for class president
    *if leadership > 15
      You win the election.
      *finish
    You lose the election.
    *finish
```

Using variables, the player’s earlier leadership choices can have an effect on the story later in the game.

You can also add leadership points to the current number of leadership points, like this:

```
  *set leadership +20
```

This would add 20 points to the player’s current leadership score. It’s the same thing as writing *set leadership leadership+20. You can also subtract points with “-“, multiply with “*” or divide with “/”.

If you need to use multiple operators at once (e.g. you need to do both division and addition), you must use parentheses, like this: *set honesty (leadership + manners)*2. You may not omit the parentheses, even though it’s perfectly understandable arithmetic: *set honesty leadership + manners / 2.

You can also show the player’s current leadership score by using ${} (a dollar sign followed by curly braces), like this:

```
  Your leadership score is: ${leadership}
```

You can also display variables on the stats screen, available when you click the “Show Stats” button. There’s a lot to discuss there, so we’ve pulled it out into a separate page: Customizing the ChoiceScript Stats Screen

By the way, variables aren’t just for numbers. You can also put text in a variable by using quotation marks:

```
  *set lover_name "Jamie"
```

And you can also set true/false “boolean” variables, which are useful because they can make your *if statements nice and short.

```
*create lover true
*if lover
  I'm a lover, not a fighter.
```

### Using *else and *elseif to Improve Readability

We can rewrite the leadership example above to use the *else command; this will make it easier to read.

```
  #Run for class president
    *if leadership > 15
      You win the election.
      *finish
    *else
      You lose the election.
      *finish
```

This does exactly the same thing as before, but using *else makes it clearer that only one of these two options is possible, just by indenting the code.

You can also use the *elseif command to define three possible branches, like this:

```
  #Run for class president
    *if leadership > 25
      You win the election by a landslide!
      *finish
    *elseif leadership > 15
      You win the election, but just barely.
      *finish
    *else
      You lose the election.
      *finish
```

## What Happens When We *finish?

When we *finish, we move on to the next scene in the game. This is defined using the *scene_list command at the top of startup.txt. Here’s an example:

```
*scene_list
  startup
  animal
  variables
  ending
  death
```

If you *finish in the “startup” scene, we’ll move right ahead to the “animal” scene, then the “variables” scene.

If you’d like to create a new scene, you’ll need to create a new txt file in the mygame folder.

Finally, we reach the ending scene. Here’s an example ending scene:

```
  This is the last scene!  The game is over!

  *ending
```

That final *ending command instructs the game to insert a “Play Again” menu at the end of the scene. If you choose to “Play Again”, the game will begin again at the “startup” scene. If you *finish in a scene that doesn’t appear in the *scene_list or if you *finish in the last scene of the game, the game will automatically insert a “Play Again” menu as if you had used the *ending command instead.

You’re not required to use *scene_list and *finish to move on to the next scene; you can also jump to any scene in the game using *goto_scene. Here’s an example:

```
  #Lift weights
    *if strength > 15
      You lift the weights.
      *finish
    You drop the weights and hurt yourself badly.  You never recover.

    *goto_scene death
```

When this happens, we jump directly to the death.txt file. This allows you to provide a standard “death” message without copying and pasting all over the game.

You can use the *goto_scene label to go to a specific *label in another scene, like this:

```
    *goto_scene invitations cordial
```

That would go to the invitations.txt file and automatically go to *label cordial within that file.

Creating new scene txt files can break accented letters (ñáéç): There are several different kinds of “plain text” files. The different kinds of txt files are called “encodings.” Each encoding handles accented letters differently. ChoiceScript uses the “UTF-8” encoding. If you create a scene using a different encoding, accented letters in your file may appear to be broken, like this: “�”.

By default, if you “Save As…” in Notepad, it will create a plain text file using the “ANSI” encoding. (There’s an “Encoding:” option on the Save As screen.) Be sure to set your encoding to “UTF-8” before saving.

## Examples

Here some example scenes from Choice of the Dragon. Please don’t copy their code without explicit permission from Choice of Games.

- startup

- queenpolitics

## Next: Other Important Commands and Techniques

## Questions?

Please post on the ChoiceScript forum if you have questions about this document.

## Make Your Own Games

- User-Made Games

- Introduction to ChoiceScript

- Important ChoiceScript Commands and Techniques

- Customizing the ChoiceScript Stats Screen

- Testing ChoiceScript Games Automatically

- Exporting and Publishing Your Game

- Achievements in ChoiceScript

- Advanced Choicescript

- Let Us Host Your ChoiceScript Games

- We Don’t Use AI

### We’re Looking for Writers

Are you a writer? Want to be one? Try your hand at writing a piece of interactive fiction for us!

 learn more

### Vampire: The Masquerade

In partnership with World of Darkness and Paradox Interactive, we're proud to announce four games based on Vampire: The Masquerade!

 learn more

 Facebook Instagram Tumblr
Contact Us

©2026 Choice of Games LLC Privacy Policy
