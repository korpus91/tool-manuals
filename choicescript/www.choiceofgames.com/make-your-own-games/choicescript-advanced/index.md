# Advanced Choicescript - Choice of Games LLC

- About Us

- Our Games

- Blog

- Forum

- Make Your Own Games

- Hosted Games

- Sign In

# Advanced Choicescript

A guide to more advanced features in the ChoiceScript programming language. Please post on the ChoiceScript forum if you have questions about this document.

## Don’t Start Here!

Be sure to read our basic ChoiceScript Introduction page before reading this advanced documentation

## Even More Commands

- *line_break: Put just one line break in your text, like a <br> in HTML. Normally you shouldn’t use this command; just press your Enter key twice and ChoiceScript will automatically insert a paragraph break. But ChoiceScript will automatically glue lines together unless they have a paragraph break; when you want something smaller than a paragraph break, just a single line break, use *line_break.
```
  So
  this
  is
  all
  one
  line.

  But this is a new paragraph.

  And this
  *line_break
  is two lines.
```

That code would display like this:

So this is all one line

But this is a new paragraph.

And this
is two lines

- *input_number: Just like *input_text, but only numbers are allowed in the text box. Specify a variable name as well as a minimum and a maximum.
```
  How many coins?
  *input_number coins 0 30

  You asked for ${coins} coins.
```

- *rand: Set a variable to a random number. You set the minimum and maximum, we do the rest. For example, this would set the variable die_roll to a value from 1 to 6 inclusive:
```
  *rand die_roll 1 6
```

Beware! Randomness can make your game much harder to test and debug, and the benefits of randomness are often overrated. From the first-time player’s perspective, there’s no difference between a non-random secret number and a randomized number. (The difference only becomes apparent when you play the game multiple times, which many people never do, particularly for longer games.)

For these reasons, we recommend using randomness sparingly, perhaps even as a last resort.

- *bug: This command causes the game to stop and crash with a specific error message. More information is available in our guide to testing ChoiceScript games automatically.
```
  *if someone_murdered and (victim = "none")
    *bug Someone was murdered, but there's no victim!
```

- *redirect_scene: This command behaves kinda like *goto_scene, but you can only use it on the stats screen. On the stats screen, the game is in “stats mode,” and so the button at the top of the screen says “Return to the game” instead of “Stats.” Stats mode is like the Matrix; it’s not the real world. In stats mode, *goto_scene stays in stats mode, and it doesn’t affect the main game. If you “Return to the game,” you’ll be right back in “game mode” in the chapter where you left off, like waking from a dream. Use *redirect_scene on the stats screen to *goto_scene in the main game.

- *looplimit: It’s possible to write an “infinite loop” bug in ChoiceScript, where the game keeps running the same lines of code over and over again, forever. These bugs can be hard to find and fix. If your game has an infinite-loop bug, you’ll see an error like this. “startup line 31: visited this line too many times (1000)” This error occurs when a line has been run (“visited”) 1,000 times in a single playthrough, which is a strong indication that your game has an infinite loop. Without this, ChoiceScript would just hang forever if you hit an infinite loop. If you actually want to run a line 1,000 times in a single playthrough, there’s a command to support that, *looplimit, which you can use like this:
```
  *looplimit 1000000000
```
 *looplimit lets you raise or lower the limit to any number you like. You can can also turn off the looplimit with *looplimit 0, but we don’t recommend it. Running a line a billion times should be good enough for anybody. (The maximum possible looplimit is approximately one trillion (12 zeroes), but, seriously?!)

- *create_array: This command is a shortcut for typing *create a bunch of times. You give it a length and a value for all of the variables, like this: *create_array attributes 5 50 and it will behave as if you’d written this:
```
  *create attributes_1 50
  *create attributes_2 50
  *create attributes_3 50
  *create attributes_4 50
  *create attributes_5 50
  *create attributes_count 5
```
 You can also provide values for each of the variables, like this: *create_array attributes 5 10 20 30 40 50.

- *temp_array: This command is just like *create_array, above, but it uses *temp instead of *create.

## Tricks with Checkpoints

- Check whether *save_checkpoint has happened yet: If you *restore_checkpoint before you *save_checkpoint, your game will fail with an error:
```
  startup line 48: Invalid *restore_checkpoint; we haven’t saved a checkpoint
```

You can use a magic variable called choice_saved_checkpoint. It starts out false, but when you *save_checkpoint, it turns true.

(Alternately, consider adding a *save_checkpoint right at the start of your game, which will ensure that *restore_checkpoint never fails.)

- Run some code after restoring from a checkpoint: *save_checkpoint will set a temp variable called choice_just_restored_checkpoint and set it to false. *restore_checkpoint will set choice_just_restored_checkpoint to true during the restoration process.
```
*save_checkpoint
*if choice_just_restored_checkpoint
    You just restored!
```

- Exclude some stats/temps from being restored: Some games track the number of times that you restore from a previous checkpoint, in order to deduct “points” for using the checkpoint, or to limit the number of times you can restore.
*restore_checkpoint will look for a variable named checkpoint_exclusions, like this:

```
*create checkpoint_exclusions "experience_points courage wisdom"
```

The excluded variables will not revert back to their old values when you *restore_checkpoint.

```
*create checkpoint_uses 0
*create checkpoint_exclusions "checkpoint_uses"

*save_checkpoint
*if choice_just_restored_checkpoint
    You just restored!
    *set checkpoint_uses +1

You have restored from the checkpoint ${checkpoint_uses} times.

...

*choice
    #Continue to the next chapter.
        *finish
    #Restore to the previous checkpoint.
        *restore_checkpoint
```

- Multiple checkpoint “slots”: When you use *save_checkpoint or *restore_checkpoint, you can specify the name of a checkpoint “slot.” This allows you to set multiple checkpoints, allowing players to go back a lot, or just a little.
```
*save_checkpoint major
...
*save_checkpoint minor
...

*choice
    #Go back a little
        *restore_checkpoint minor
    #Go way, way back
        *restore_checkpoint major
```

(Each checkpoint slot gets its own variable. In this example, choice_saved_checkpoint_major would be set to true when you *save_checkpoint major.)

- Restore to the last checkpoint at any time from the stats screen: You can write code to restore from the stats screen like this:
```
[choicescript_stats.txt]
*stat_chart
    ...

*choice
    #Done.
        *finish
    *if (choice_saved_checkpoint) #Restore from the last checkpoint.
        *restore_checkpoint

```

Note that you’ll need *if (choice_saved_checkpoint) to make sure the player doesn’t try to restore before the first checkpoint has been set.

- Player-named save slots: You can write code to allow players to name their own save slots.
```
*create_array save_name 3 "[empty]"
*create checkpoint_exclusions save_name_1 save_name_2 save_name_3

...

*gosub save

...

*gosub restore

...

*label save
*temp slot
Which slot do you want to save?
*choice
    #Slot 1: ${save_name_1}
        *set slot 1
    #Slot 2: ${save_name_2}
        *set slot 2
    #Slot 3: ${save_name_3}
        *set slot 3
What do you want to call your saved game?
*input_text save_name[slot]
*if slot = 1
    *save_checkpoint slot1
    *return
*if slot = 2
    *save_checkpoint slot2
    *return
*if slot = 3
    *save_checkpoint slot3
    *return

*label restore

*choice
    *selectable_if (choice_saved_checkpoint_slot1) #Slot 1: ${save_name_1}
        *restore_checkpoint slot1
    *selectable_if (choice_saved_checkpoint_slot2) #Slot 2: ${save_name_2}
        *restore_checkpoint slot2
    *selectable_if (choice_saved_checkpoint_slot3) #Slot 3: ${save_name_3}
        *restore_checkpoint slot3
    #Cancel
        *return
```

## The ChoiceScript IDE

The ChoiceScript IDE is a powerful integrated development environment for the ChoiceScript language. It includes a code editor for writing and scripting, a built-in copy of ChoiceScript (and both of its automated tests), for testing and running your game side-by-side with your code. It will log errors and highlight (and focus) on the problematic lines, spell-check your work and even handle your indentation for you.

Note that the ChoiceScript IDE is not developed or maintained by Choice of Games. If you have questions about the ChoiceScript IDE, direct your questions to the IDE team via the ChoiceScript IDE discussion thread.

## More Conditional Options

In addition to using *if on each line, you can also use nested blocks of conditionals. This technique is pretty advanced, because it’s hard to get the indentation exactly right.
```
  *choice
    #Rattle my saber.
      They rattle back.
      *finish
    *if republican
      *if president
        #Declare open war.
          Congress refuses to approve funding.
          *finish
      *else
        #Ask other Republicans to help out.
          Talk radio is on your side.
          *finish
    *else
      *if president
        #Work with the United Nations.
          Russia vetoes your plan.
          *finish
      *else
        #Ask other Democrats to help out.
          They do their best, but the party is divided.
          *finish

```

## *hide/disable_reuse Globally

You can make all options non-reusable, by adding *hide_reuse or *disable_reuse to the top of your ChoiceScript file. Then you can use the *allow_reuse command to allow certain options to be reused.
```
  *hide_reuse
  *label start
  *choice
    #One.
      The loneliest number that you'll ever do.
      *goto start
    #Two.
      Two can be as bad as one.
      *goto start
    *allow_reuse #I can't decide!
      Well, think it over.
      *goto start
    #Done.
      OK!
      *finish

```

## Math

- Integer math: You can round a variable to the nearest integer using round(). For example, this will set the variable “foo” to 3: *set foo round(2.5)You can also use the modulo operator calculate the remainder after taking a division. Modulo is pretty weird, but it’s has two particularly interesting uses. First, you can check whether a number X is evenly divisible by a number Y by checking whether X modulo Y = 0. Second, you can use it to get the fractional part of a number X, the stuff that comes after the decimal point, by calculating X modulo 1. For example, 3.14 modulo 1 = 0.14.

- Exponents and logarithms: You can use exponents like this: *set foo 3^7. That will set foo to 2,187 (three to the seventh power).You can also compute a logarithm (base 10) like this: *set foo log(1000). (You can always divide to use a different logarithm base e.g. *set foo log(2187)/log(3))

## Text tricks

- Capitalize: You can capitalize just the first letter of a variable like this: Behold! $!{He} is capitalized. You can also capitalize an entire word like this: PRESIDENT $!!{name} RESIGNS IN SHAME

- Bold and italic: You can write text in bold or italic like this: This is [b]bold[/b] and this is [i]italic[/i].

- Using ${} in quoted strings: You can use variables in quoted strings, like this: *set name "Dr. ${last_name}"

- Concatenation: You can join text together like this: *set murder "red"&"rum"..

- Quotes: You can put quotes in your text by using backslashes, like this:
```
  *set joke "she said it was \"ironic\"!"
```

If you write ${joke}, you’ll get:

she said it was “ironic”!

- Backslashes: You can put backslashes in your text by using even more backslashes, like this:
```
  *set slashy "Here's one backslash: \\ and here's two backslashes: \\\\"
```

If you write ${slashy}, you’ll get:

Here’s one backslash: \ and here’s two backslashes: \\

- Characters: You can extract the characters (letters/numerals) out of a variable, like this:
```
  *temp word "xyzzy"
  *temp first_letter word#1
  *temp second_letter word#2
  The first letter of the word "${word}" is ${first_letter} and the second letter of the word is ${second_letter}.
```

- Counting characters: You can count the number of characters in a word like this:
```
  *temp word "plough"
  *temp word_length length(word)
  *temp last_letter word#word_length
  The word "${word}" is ${word_length} letters long, and so its last letter is ${last_letter}.
```

## Gosub Parameters

After the *gosub label, you can include any number of parameters. When you use the *params command, it sets temps named param_1, param_2, etc. for each parameter. (It also sets a param_count temp with the number of parameters; in this case, param_count would be 2.)

```
  *gosub visit "Dracula" "garlic"

  *label visit
  *params
  You go to visit ${param_1} and you bring ${param_2} with you.
  *return
```

Since param_1 and param_2 are not very good names, you might be tempted to write some code like this:

```
  *params
  *temp person param_1
  *temp gift param_2
```

We anticipated that; you can just write the names of the parameters after *params and we’ll set the temps for you, like this:

```
  *label visit
  *params person gift
  You go to visit ${person} and you bring ${gift} with you.
  *return
```

You can also use parameters with *gosub_scene. *gosub_scene allows you to optionally specify a label, e.g. *gosub_scene travel visit so if you want to pass in parameters to *gosub_scene, you must specify a label name. *gosub_scene visit "Dracula" won’t use a parameter; it will try to *gosub the label Dracula.

Programmer-ish people should note that parameters are just ordinary *temps and are scoped to the entire file, not the subroutine. Thus, if you *gosub within a *gosub, param_1 can and will be changed in the second subroutine and will not be restored when you *return.

However, *gosub_scene defines a new scope for *temp, so if you want your *params to be scoped to the subroutine, (for example if you want to use recursion,) you can use *gosub_scene instead of *gosub.

Here’s an example of a naive recursive subroutine to compute the Fibonacci sequence. (Note that it can only work with *gosub_scene; it wouldn’t work with *gosub because of parameter scopes.)

```
  *create return 0

  *gosub_scene startup fib 6
  ${return}

  *finish

  *label fib
  *params n
  *if n < 2
    *set return 1
    *return
  *gosub_scene startup fib (n-1)
  *temp prev return
  *gosub_scene startup fib (n-2)
  *set return +prev
  *return
```

## Truly bizarre references

Probably only programmers will appreciate these. Beware! They add complexity without adding much value.

- Curly parens: Put some text in curly braces and we’ll turn it into the value of the named variable.
```
  *set honesty 30
  *set virtue "honesty"
  *set score {virtue}
  Your ${virtue} score is ${score}
```

This would print:

Your honesty score is 30

You could also just write: Your ${virtue} score is ${{virtue}}.

- Set by reference: Set a variable by name, e.g. *set {"leadership"} 30 sets leadership to 30. Use it in crazy code like this:
```
  *set virtue "courage"
  *set {virtue} 30
```

This code would set courage to 30. If this still doesn’t seem useful, consider that virtue could have been determined by earlier choices, so it might have set honesty to 30 instead. You can also use it with *rand, *input_text, and *input_number.

Still not convinced? Don’t worry about it; you’ll probably never need it.

- Goto a label by name:
```
  *temp superpower "invisibility"
  Your super power is:
  *goto {superpower}
  flight!
  *finish
  *label invisibility
  invisibility.
```

You can also use this with *goto_scene and *gosub_scene. Beware that Quicktest effectively skips *goto_scene and *gosub_scene lines that use curly references. (Randomtest works fine.) If you have a file with a section that can only be reached using a curly referenced *goto_scene command, consider adding a section like this somewhere in your game, enumerating the possible destinations.

```
  *if false
    *gosub_scene checkpoint chap1
    *gosub_scene checkpoint chap2
    *gosub_scene checkpoint chap3
```

Quicktest will “run” those lines to verify that the chap1, chap2, and chap3 labels exist in the checkpoint scene, and verify that those labels will be actually covered by Quicktest.

- Array brackets: You can put square brackets after the name of a variable, like this: foo[1], to refer to the variable foo_1. But you can put anything in the brackets, including variables, like this: strength[current_opponent].
```
  *create current_opponent 1
  *create_array strength 5 50
  *create_array damage 5 20
  You did ${damage[current_opponent]} points of damage.
  *set strength[current_opponent] -damage[current_opponent]
  *goto dialog[current_opponent]
  *gosub_scene dialog[current_opponent] took_damage
```

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
