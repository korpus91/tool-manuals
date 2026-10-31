# Testing ChoiceScript Games Automatically - Choice of Games LLC

- About Us

- Our Games

- Blog

- Forum

- Make Your Own Games

- Hosted Games

- Sign In

# Testing ChoiceScript Games Automatically

Interactive novels written in ChoiceScript can be very hard to test, because each *choice point can create new variations of the game that need testing. When testing by hand, it can be hard to be certain whether some path of choices can cause the game to crash, or whether some important part of the story can’t be reached at all.

To help with this, we’ve developed two tools that can make debugging ChoiceScript games considerably easier.

- Randomtest: The Randomtest tool automatically plays your game over and over, making random decisions for every choice, and generates a “hit count” report, which tells you how many times each line of code was used in random play.

- Quicktest: Instead of running the code at random, Quicktest attempts to test every #option in every *choice, and both sides of every *if statement. In order to do this quickly, Quicktest “cheats” by skipping lines that it has already tested.

- Keyboard Shortcuts: When playing the game manually, you can use keyboard shortcuts to click the Next button, allowing you to bang on the keyboard to quickly playthrough a game from beginning to end.

All types of tests are necessary. Quicktest can find some bugs that Randomtest can’t find, and vice versa. Unfortunately, Quicktest can also find some “fake” bugs — problems with code style that could cause a problem, but don’t actually do any harm for actual players. And, of course, nothing can ever truly replace manual testing!

- Keyboard Shortcuts

- Running the Tests

- Quicktest: Interpreting Error Messages

- Detecting Dead Code

- Fake Bugs in Quicktest

- The *bug Command

- Randomtest Options

- Randomtest Game Log

- Randomtest Hit Count

- Forcing Randomtest to Make Certain Choices

## Keyboard Shortcuts

The “Next” button in ChoiceScript has a browser accesskey. The actual keyboard shortcut depends on whether you’re on Windows or macOS.

As of September 2020, the keyboard shortcut for the “Next” button is as follows for Chrome, Firefox, and Safari:

- Windows: Alt-Shift-N for Next, Alt-Shift-number to select an option

- macOS: Control-Option-N for Next, Control-Option-number to select an option (note this shortcut uses the Control key ^, not the Command key ⌘)

These shortcuts allow you to hold down Alt+Shift or Control+Option and then tap N repeatedly to speedrun your way through a game. While you’re doing that, you might want to click the “Settings” button at the top of the screen and select “Don’t animate between pages,” to make the game run a bit faster.

## Running the Tests

If you followed the ChoiceScript introduction, you’ll see two “Tests” links at the bottom of the page, for “Quicktest” and “Randomtest.” When you click the “Quicktest” link, Quicktest will run immediately. When you click the “Randomtest” link, it will ask you a few questions. (See Randomtest Options, below.)

You can also run the tests by double-clicking on files in the ChoiceScript folder. (But finding and using those files is a little more complicated than just clicking on links in your browser.)

On Windows, you can run the tests by double-clicking on the included run-randomtest.bat and run-quicktest.bat files. (If Windows SmartScreen Defender gives you trouble, click More Info, Run Anyway.)

On a Mac, you’ll need to use randomtest.command and quicktest.command. (If you get the “can’t be opened because it is from an unidentified developer” error, hold Control, click on the file, and click Open.)

## Quicktest: Interpreting Error messages

If Quicktest passes, it will say “QUICKTEST PASSED” on the console. If not, it will print out an error message.

```
Error: startup line 16: Non-existent command 'oops'
```

In this example, I added a broken line *oops on line 16 of a ChoiceScript file, and this is what it printed out.

If Quicktest (or ChoiceScript) gives you an error message that you can’t understand, feel free to ask us about it on our forums. Be sure to post not only the error message, but also the entire file of code that causes the problem. If you don’t want to share that much code with the group, you can also just send the code to us at support@choiceofgames.com; we’ll do our best to help you out.

## Detecting Dead Code

But even if Quicktest passes, it may still report a number of lines untested, e.g.

```
13 UNTESTED startup
18 UNTESTED startup
19 UNTESTED startup

SOME LINES UNTESTED
QUICKTEST PASSED
```

If Quicktest says “SOME LINES UNTESTED,” it means that Quicktest thinks those lines are completely unreachable. Those lines are “dead code,” that no player can ever see.

For example, here’s a way to introduce dead code without noticing it. We start with code like this:

```
*set leadership %+ 20
*goto big_speech
```

But then later we realize we also want to decrease strength. Foolishly, we just add a line at the end, like this:

```
*set leadership %+ 20
*goto big_speech
*set strength %-15
```

That *set strength %-15 line is dead code; it can never be reached, because it comes immediately after a *goto.

When Quicktest finds dead code, you should fix the problem, either by deleting the code or by fixing the bug that kills the code. In this example, we’d probably just move the *goto line down to the end.

Note that Quicktest isn’t guaranteed to find all dead code… due to the way Quicktest “cheats,” it can sometimes reach code that normal human players can’t reach. Use Randomtest to find some of the other dead code in this system.

## Fake Bugs in Quicktest

tl;dr: You may need to turn some of your *if statements into *else statements to get Quicktest to pass.

Quicktest automatically plays through the code as a normal player would, but when encountering a *choice statement or an *if statement, Quicktest makes multiple copies of itself and attempts to run them. (The copies run one at a time; for example, we test the true lines of an *if statement before we test the *else lines.)

To save time, Quicktest “cheats.” If one copy of Quicktest verifies a line of code, and then a later copy of Quicktest reaches the same line of code, the second copy of Quicktest will quit, assuming that the earlier copy of Quicktest has already done its job.

But Quicktest “cheats” in another way, too, by testing both sides of *if statements even if the lines are not actually possible for a player to reach. This can cause Quicktest to identify “fake” bugs: bugs that can’t actually happen in real life.

For example, ChoiceScript attempts to guarantee correctness by requiring every #option in a *choice statement to end with *goto or *finish. Quicktest can help you catch bugs like this:

```
Example 1 (Buggy)

*choice
    #Be very naughty.
        Santa refuses to give you a present.
    #Be mostly nice.
        Santa gives you a present reluctantly.
    #Be as nice as can be.
        Santa gives you a present enthusiastically.

Inside the gift box is a video game!
```

If ChoiceScript allowed this code, it would create a hard-to-detect bug; if you’re very naughty, you still get a video game. Instead, ChoiceScript crashes if you write code like this; Quicktest can detect the crash automatically, allowing you to catch the bug easily.

You can fix the code like this:

```
Example 2 (Fixed)

*choice
    #Be very naughty.
        Santa refuses to give you a present.
        *finish
    #Be mostly nice.
        Santa gives you a present reluctantly.
        *goto present
    #Be as nice as can be.
        Santa gives you a present enthusiastically.

*label present
Inside the gift box is a video game!
```

But now suppose we included an *if statement in the middle of this *choice. Suppose we have a politics variable, which we set to either “democrat” or “republican”. Then we might write code like this:

```
Example 3 (Politics Bug)
*choice
    #Be very naughty.
        Santa refuses to give you a present.
        *finish
    #Be mostly nice.
        *if politics = "democrat"
            *goto democrat_present
        *if politics = "republican"
            *goto republican_present
    #Be as nice as can be.
        Santa gives you a video game.
```

This code has a bug, but it might never happen in real life: what if politics is neither “democrat” nor “republican?”

If a political independent were playing through Example 3, the game would crash, with the same error as Example 1; Quicktest automatically detects that.

Here’s how: at the first *if statement, Quicktest creates a copy of itself: it starts with one copy where politics = "democrat", and then another copy where politics != "democrat"; that non-Democrat copy then makes a copy of itself, one where politics = "republican" and another copy where politics != "republican".

In that final copy, Quicktest tests the case where politics is neither “democrat” nor “republican”; since there is no *goto or *finish in that case, Quicktest crashes with an error.

Now, in your game, you may not actually have any other political parties. But Quicktest can’t know that for sure, so Quicktest will say that Example 3 is buggy, even if there’s a 0% chance of the bug occurring in real life.

You can fix Example 3 with an *else statement, which helps Quicktest to understand that there are only two possibilities in this case:

```
Example 4 (Politics Fixed)
*choice
    #Be very naughty.
        Santa refuses to give you a present.
        *finish
    #Be mostly nice.
        *if politics = "democrat"
            *goto democrat_present
        *else
            *goto republican_present
    #Be as nice as can be.
        Santa gives you a video game.
```

Here, Quicktest only makes two copies: one where politics = "democrat" and another where poliics != "democrat". The *else guarantees no other possibilities.

You can also fix “fake” Quicktest failures using the *bug command, below.

## The *bug Command

ChoiceScript includes a *bug* command, which causes the game to crash with a specific message.

```
*if someone_murdered and (victim = "none")
    *bug Someone was murdered, but there's no victim!
```

The *bug command can be especially useful with Randomtest, which can tell you an exact set of steps that it used to reach the *bug.

Beware, if a user actually encounters a *bug in normal play, the game will stop with an error message, so you’ll want to run Randomtest to make sure the *bug lines can never be reached.

It might surprise you to learn that the *bug command is ignored by Quicktest. This is necessary due to the way Quicktest “cheats.” Quicktest will always run both sides of every *if statement, regardless of which side is actually true. So Quicktest will necessarily run the *bug command one way or another. When it does, that wayward copy of Quicktest will just halt, without reporting an error.

That means that you can fix Example 3 from the previous section with a *bug statement, like this:

```
Example 5 (fixed with a *bug)
*choice
    #Be very naughty.
        Santa refuses to give you a present.
        *finish
    #Be mostly nice.
        *if politics = "democrat"
            *goto democrat_present
        *if politics = "republican"
            *goto republican_present
        *bug Politics should only be Democrat or Republican!
    #Be as nice as can be.
        Santa gives you a video game.
```

When the copy of Quicktest that is neither Democrat nor Republican hits that *bug line, Quicktest will stop and ignore the *bug. Of course, this is no proof that the bug won’t actually occur in real life; if the game includes politics other than “democrat” or “republican”, then we would need to run Randomtest to automatically report the *bug error.

Thus, it’s arguably safer to fix Quicktest “fake bugs” with *else as in Example 4 above, because that guarantees that the code will not crash for real users.

## Randomtest Options

- Iterations: When you launch Randomtest, it will ask you how many times you’d like to run it. We recommend running it 10,000 times or more for adequate testing.
- Starting seed number: Note: Randomtest is not truly random. In fact, Randomtest’s output is completely deterministic; if you run it twice in a row, you’ll get exactly the same results both times. This catches a lot of people by surprise. (Specifically, Randomtest is using a pseudo-random number generator with a hard-coded “seed” value.)
Doing it this way has one big advantage: if Randomtest fails with an error and you run it again, it will fail again with the same error. If you fix a bug and Randomtest passes, you can be sure that you’ve fixed that problem.

As a result, if you want to run 30,000 random playthroughs with Randomtest, it won’t work to just run Randomtest three times; you’ll just play the same 10,000 variations over again. Instead, you’ll need to run 30,000 iterations, or at least set the “starting seed number” to “10000” or “20000” each time you run it.

- Avoid used options: In this mode, when Randomtest encounters a *choice that it’s seen before, it will count the number of times each option has been used, and it will choose the option that has been tested the least, choosing randomly only in the case of a tie.
Avoiding used options is less random, but it typically finds bugs faster. One drawback is that some bugs can only be caught when you select the same option multiple times in a row, which Randomtest will never do when it’s avoiding used options.

- Show full text during the game: The Randomtest log can be rather long, and it can be extra, extra long if we include every word that the player sees. If you need more details to help you find a tricky bug, turn on “show full text.”

- Show choices selected during the game: If your Randomtest log is really really long, you can hide the list of choices that Randomtest makes.

- Highlight gender pronouns: If your game has variable gender pronouns, it can be easy to accidentally type “he” when you meant to type “${he}“. If you highlight gender pronouns and show full text, we’ll show pronouns in a different color, highlighted in blue when the pronoun is a variable, like “${he}“, and highlighted in red when the pronoun is hard-coded in the text, like “he“.

- After the test, show how many times each line was used: After the test passes, Randomtest can print out a “hit count” of how many times each line was hit. (See below for details.)

- Automatically scroll to the bottom: Automatically scrolls the page to the bottom as Randomtest is running.

## Randomtest Game Log

Randomtest can generate a huge log of everything it randomly tries.

Here’s a sample of the first part of the Randomtest log, generated from our example game provided with ChoiceScript.

```
    *****Seed 0
    startup *choice 55#3 (line 83) #Abdicate the throne. I have clearly mismanaged this kingdom!
    animal *choice 19#1 (line 20) #Lion
    variables *choice 22#2 (line 26) #Strength
    variables *choice 31#1 (line 32) #Run for class president
    gosub *choice 5#2 (line 13) #Give him my lunch money.
    gosub *choice 24#2 (line 28) #Sad.
    *****Seed 1
    startup *choice 55#1 (line 56) #Make pre-emptive war on the western lands.
    startup *choice 59#2 (line 64) #Appoint charismatic knights and give them land, peasants, and resources.
    animal *choice 19#3 (line 26) #Elephant
    variables *choice 22#1 (line 23) #Leadership
    variables *choice 31#2 (line 38) #Lift weights
    *****Seed 2
    startup *choice 55#2 (line 72) #Beat swords to plowshares and trade food to the westerners for protection.
    startup *choice 75#1 (line 76) #Accept the terms for now.
    animal *choice 19#2 (line 22) #Tiger
    variables *choice 22#2 (line 26) #Strength
    variables *choice 31#2 (line 38) #Lift weights
    gosub *choice 5#1 (line 6) #Stand up to him.
    gosub *choice 24#1 (line 25) #Angry.
```

The *****Seed lines tell you when Randomtest finished a playthrough and started over again on its next playthrough. The other lines specify which exact choices Randomtest made while playing through the game.

For example, the line startup *choice 55#3 (line 83) says that in the file startup.txt there was a *choice on line 55. The rest of the line indicates which option Randomtest chose, and the line number of that option. In this example, Randomtest chose option #3 on line 83. In the second playthrough, we see startup *choice 55#1 (line 56) which says that Randomtest instead chose option #1 on line 56.

Ideally, the last line of randomtest-output.txt says “RANDOMTEST PASSED.” If not, it contains an error message; see “Interpreting Error Messages” above for additional details. But note that you can use the Randomtest log to tell you exactly how to reproduce the bug by hand: just make the exact same choices that Randomtest did (“option #1, #2, #3, #1, #2 …”) before the error occurred. Reproducing Randomtest bugs by hand can make them much easier to understand and fix.

## Randomtest Hit Count

Randomtest offers to show you show how many times each line was used. Each time a line is used, we say that the line was “hit,” and the report of how many times each line was hit is called a “hit count.”

If you choose to generate a hit count, it’s usually the longest part of the output.

For example, here’s a sample from the hit count for the startup.txt example run 10,000 times:

```
startup 10000: Your majesty, your people are starving in the streets, and threaten revolution.
startup 10000: Our enemies to the west are weak, but they threaten soon to invade.  What will you do?
startup 10000:
startup 10000: *choice
startup 10000:   #Make pre-emptive war on the western lands.
startup 3418:     If you can seize their territory, your kingdom will flourish.  But your army's
startup 3418:     morale is low and the kingdom's armory is empty.  How will you win the war?
startup 3418:     *choice
startup 3418:       #Drive the peasants like slaves; if we work hard enough, we'll win.
startup 1133:         Unfortunately, morale doesn't work like that.  Your army soon turns against you
startup 1133:         and the kingdom falls to the western barbarians.
startup 1133:         *finish
startup 3418:       #Appoint charismatic knights and give them land, peasants, and resources.
startup 1132:         Your majesty's people are eminently resourceful.  Your knights win the day,
startup 1132:         but take care: they may soon demand a convention of parliament.
startup 1132:         *finish
startup 3418:       #Steal food and weapons from the enemy in the dead of night.
startup 1153:         A cunning plan.  Soon your army is a match for the westerners; they choose
startup 1153:         not to invade for now, but how long can your majesty postpone the inevitable?
startup 1153:         *finish
startup 10000:   #Beat swords to plowshares and trade food to the westerners for protection.
startup 3278:     The westerners have you at the point of a sword.  They demand unfair terms
startup 3278:     from you.
startup 3278:     *choice
startup 3278:       #Accept the terms for now.
startup 1601:         Eventually, the barbarian westerners conquer you anyway, destroying their
startup 1601:         bread basket, and the entire region starves.
startup 1601:         *finish
startup 3278:       #Threaten to salt our fields if they don't offer better terms.
startup 1677:         They blink.  Your majesty gets a fair price for wheat.
startup 1677:         *finish
startup 10000:   #Abdicate the throne. I have clearly mismanaged this kingdom!
startup 3304:     The kingdom descends into chaos, but you manage to escape with your own hide.
startup 3304:     Perhaps in time you can return to restore order to this fair land.
startup 3304:     *finish
```

Randomtest played 10,000 iterations, so you can see the intro and the option text was displayed all 10,000 times. There are three options (“war”, “trade”, and “abdicate”) each of which was hit approximately one third of the time: Randomtest hit “war” 3,418 times, “trade” 3,278 times, and “abdicate” 3,304 times.

Under “war” there are three sub-options; those options divided the 3,418 “war” hits approximately into thirds: 1,133, 1,132, and 1,153. Under “trade” there are only two sub-options; those options divided the 3,279 “trade” hits in half: 1,601 and 1,677.

If the hit count report tells you that some lines were hit zero times, that suggests that the lines might be “dead” code — code that can’t be reached no matter what choices the player makes. However, code with 0 hits doesn’t guarantee that the code is dead — it could just be very difficult to reach.

If you find code that’s hard to reach, you’ll have to decide for yourself whether that indicates you have a bug. For example, in the traditional “choose a path” books, it was very hard to reach a “good” ending; most endings had a bad outcome (e.g. death). On the one hand, that might be a good thing, if it encourages players to try again; on the other hand, it might be frustrating to keep reaching bad endings.

To pick another example, if your choices have “right” and “wrong” answers (e.g. if your game has a lot of puzzles in it), Randomtest may tell you that it’s very unlikely to win your game when playing randomly. But that may be ideal; if you can beat the game just by random choices, your puzzles may be too easy!

When interpreting the hit count report, remember that you can divide the hit count by 10,000 to get the percentage likelihood of hitting a given line. If a line is hit less than 100 times, then there’s less than 1% chance of hitting the line at random. If that’s too low in your opinion, consider sculpting your game balance to allow more players to reach that code.

## Forcing Randomtest to Make Certain Choices

Randomtest can be quite unlike a real player; sometimes the hit count can be more useful if you force Randomtest to make certain choices.

There’s a special variable, choice_randomtest which is true if and only if the game is currently running in Randomtest. That lets you write code like this:

```
*if choice_randomtest
    *goto success

In what year was William Howard Taft elected president of the United States?

*choice
    #1908.
        *label success
        *set success true
        Correct!
        *finish
    #1909.
        No, that's the year he took office. He was elected in 1908.
        *finish
    #1912.
        No, in 1912 Taft lost the election to Woodrow Wilson.
        *finish
    #1857.
        No, that's the year Taft was born.
        *finish
```

### Randomtest is not allowed to run *restore_checkpoint

If Randomtest ran *restore_checkpoint, it would just run itself in circles, never finishing.

If Randomtest randomly stumbles upon a *restore_checkpoint command, it will fail with an error. Block it from running *restore_checkpoint like this:

```
  *choice
    #Continue to the next chapter.
      *finish
    *if (not(choice_randomtest)) #Restore to the previous checkpoint.
      *restore_checkpoint

```

## Next: Exporting and Publishing Your Game

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
