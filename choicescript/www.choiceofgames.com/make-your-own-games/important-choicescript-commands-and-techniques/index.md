# Important ChoiceScript Commands and Techniques - Choice of Games LLC

- About Us

- Our Games

- Blog

- Forum

- Make Your Own Games

- Hosted Games

- Sign In

# Important ChoiceScript Commands and Techniques

A guide of important techniques in the ChoiceScript programming language. Please post on the ChoiceScript forum if you have questions about this document.

## Don’t Start Here!

Be sure to read our basic ChoiceScript Introduction page before reading these techniques.

## Other Important Commands

- *title: This command sets the title of the game. It must be used at the top of startup.txt, along with *create and *scene_list.

```
  *title Choice of the Dragon
```

The Google Play Store for Android puts a limit of 30 characters on game titles. ChoiceScript will allow a title of any length, but if you’re planning to publish your game with us, you’ll need to come up with a name for your game that’s 30 characters or less, including spaces.

- *author: This command sets the author “by line” of the game. It must be used at the top of startup.txt, along with *create, *title, and *scene_list.

```
  *author Dan Fabulich and Adam Strong-Morse
```

- *ifid: This comand embeds an IFID (Interactive Fiction Identifier) in your game. It’s like an ISBN number for books. You’ll need to randomly generate an IFID. Luckily for you, we’ve generated one for you, like this:

```
Loading...
```

Copy and paste that line into your startup.txt file, at the top, near the *title. (Adding an IFID is required in order to support saving your progress when you export to HTML.)

- *temp: This command is very much like *create but it creates a temporary variable that only exists in the current file. Unlike *create, you can use *temp anywhere, and you’re not required to specify a starting value for a *temp variable.
```
  *temp conversation
  *set conversation "a little less"
  *temp action "a little more"
```

Note: *temp variables are erased when you *finish or when you *goto_scene. (If you want to go to another scene file without erasing your *temp variables, you might want to use *gosub_scene instead. See below.)

- *comment: This command does nothing; any text you put after *comment will be ignored. It’s helpful to put remarks in the text that only the author should read.

```
  *comment TODO We should make this scene more interesting!
```

- *page_break: Put in a “Next” button with no radio buttons. The game will continue on the subsequent page.

```
  You turn the corner slowly.  Blood rushes through your ears.  As you open the door...
  *page_break
  ... the masked murderer attacks!
```

By default, *finish buttons say “Next Chapter” and *page_break buttons say “Next”. You can make the button say something else, instead:

```
  *page_break On with the show!
  *finish The show is over!
```

We recommend no more than five words on button titles; more than that looks really weird on the screen, particularly on mobile screens.

- *input_text: Provides a text box for the user to specify the value of a variable, e.g. the user’s name.
```
  Please enter your name.
  *input_text name

  Your name is ${name}, is that right?
```

ChoiceScript won’t allow the player to leave the input blank. If you want to allow that, you can use:
```
  *input_text name allow_blank
```

- *fake_choice: This convenience command behaves exactly like *choice, but no commands are allowed in the body of the choice; thus no *goto/*finish is required.

```
  What color do you prefer?

  *fake_choice
    #Red
      Red is the color of roses.
    #Blue
      Blue is the color of the sea.
    #Green
      Green is the color of spring.

  What an excellent choice!  And what flavor of ice cream would you like?

  *fake_choice
    #Vanilla
    #Chocolate
    #Strawberry

  Mmm, delicious!
  *finish
```

- *image: This command inserts an image. Place the image in the “mygame” folder, and type the name of the image file, like this:
```
  *image beauty.jpg
```

If you like, you can specify the alignment (“left”, “right”, or “none”) after the image name, like this:

```
  *image beauty.jpg left
```

By default, the image appears centered on a line by itself, but if you align the image left or right, the text will flow around the image. (In CSS terms, the image will “float” left or right.) If you want the image to appear left-aligned on a line by itself, use “none.”

If your image is important to understanding the story (e.g. it has words on it the player needs to read), then you should type an alternate description after the alignment. This text will be accessible to users who can’t see the image, e.g. visually impaired users.

```
  *image beauty.jpg left Beauty
```

- *save_checkpoint: You can use the *save_checkpoint command to save a checkpoint. Then, later, you can give players the option to restore to a previous checkpoint with the *restore_checkpoint command, like this:

```
  *choice
    #Continue to the next chapter.
      *finish
    #Restore to the previous checkpoint.
      *restore_checkpoint
```

When you *restore_checkpoint, the player will “travel back through time” to the moment that *save_checkpoint was called.

## Percentile Stats and Fairmath

Stats that display on the stat screen usually range from 0 to 100. It can be difficult to guarantee that the player can never accidentally gains more than 100 points of leadership. To help with this, we’ve provided special commands that will keep stats in between 0 and 100.

```
*set leadership %+20
*set strength %-10
```

The “%+” and “%-” operators are called the “fairmath” operators. The idea is that as your leadership score gets higher, it becomes harder to increase, and easier to decrease. According to fairmath:

- Fair Addition: (x %+ y) = (x + (100-x)*(y/100))

- Large scores are hard to increase: (90 %+ 20) = (90 + 2) = 92

- Small scores are easy to increase: (10 %+ 20) = (10 + 18) = 28

- Fair Subtraction: (x %- y) = (x - x*(y/100))

- Large scores are easy to decrease: (90 %- 20) = (90 - 18) = 72

- Small scores are hard to decrease: (10 %- 20) = (10 - 2) = 8

- 50 is equally easy to increase or decrease.

- (50 %+ 20) = (50 + 10) = 60

- (50 %- 20) = (50 - 10) = 40

We recommend that you always/only use Fairmath to update percentages. If you’re having trouble deciding how many points to allocate using Fairmath, here are some guidelines:

- On average, Fairmath has half the effect of simple addition. So, for example, %+ 20 usually only gives the player about 10 more points.

- If you want to give a small bump, make it %+10. If you want a large boost, make it %+40.

- A player with a skill of 50% has average ability.

- A skill of 60% is good; 70% is excellent.

- 80% skill is almost impossible.

## Types of *if Statements

You can do a lot more with *if statements than leadership > 15. Here’s a few tricks:

- Equality and Inequality

- Equal to: leadership = 40 (Is leadership equal to forty?)

- Not equal to: leadership != 40 (Is leadership different from forty?)

- Greater than: leadership >40 (Is leadership greater than forty?)

- Less than: leadership <40 (Is leadership less than forty?)

- Greater than OR equal to: leadership >=50 (Is leadership greater than or equal to fifty?)

- Less than OR equal to: leadership <=40 (Is leadership less than or equal to forty?)

- And/or/not (with mandatory parentheses)

- And: (leadership > 30) and (strength > 40)

- Or: (leadership > 60) or (strength > 70)

- Not: not(strength > 70)

- Complex parentheses: ((leadership > 60) and (agility > 20)) or (strength > 80)

- Comparing text:

- lover_name = "Jamie"

- "2" = 2 (this is true!)

- Setting variables to true or false:

- *set finished false

- *set correct guess = "blue"

## Multireplace with @{}

Multireplace is a little bit like ${} replacement, but you give it a variable and a list of options. The variable must be either a number or true/false (true=1, false=2). @{} will insert the option corresponding to the number.

```
There @{count is one thing|are two things|are three things} here.
You are on the @{is_evil Dark|Light} Side of the Force.
Behold the dragon@{plural s|}!
Behold the dragon@{(dragons > 1) s|}!
Behold the dragon@{(dragons = 1) |s}!
```

The first word should be a variable name, followed by a space, and then a number of options separated by vertical pipes |. Empty options are allowed. You can also use more complex expressions by wrapping them in parentheses.

Note that the first option is numbered #1. If you want the first option to be zero, add 1 to the variable in parentheses, like this:

```
There @{(count+1) are no things|is one thing|are two things} here.
```

You can nest ${} replacements in @{} but you can’t nest @{} inside another @{}.

## Conditional Options

Sometimes we want to show players that a choice is not available to them. We can do that like this:

```
  How will you handle this?
  *choice
    #Try to talk them out of it.
      They cannot be dissuaded.
      *finish
    #Force them to relent.
      They back down, for now.
      *finish
    *selectable_if (president) #Abuse my presidential powers to silence them
      This works; you will never hear from them again.
      *finish
```

If you aren’t president, you’ll see the option to abuse presidential power, but it will appear in grey; it won’t highlight if you click on it. This gives players a hint that if they play the game again, they might be able to choose that option, by making different choices earlier on.

If we want to hide the option altogether, we can use *if instead of *selectable_if, like this:

```
  How will you handle this?
  *choice
    #Try to talk them out of it.
      They cannot be dissuaded.
      *finish
    #Force them to relent.
      They back down, for now.
      *finish
    *if (president) #Abuse my presidential powers to silence them
      This works; you will never hear from them again.
      *finish
```

In this example, if you aren’t president, you won’t even see an option to abuse presidential power.

Sometimes we just want to prevent certain options from being reused. We can do that with the *hide_reuse and *disable_reuse modifiers, like this:

```
  *label start
  *choice
    *hide_reuse #One.
      The loneliest number that you'll ever do.
      *goto start
    *disable_reuse #Two.
      Two can be as bad as one.
      *goto start
    #I can't decide!
      Well, think it over.
      *goto start
    #Done.
      OK!
      *finish

```

If the player selects #One, the option will be hidden; if the player selects #Two, the option will be unselectable (greyed out).

(Note that if you rewind time with *restore_checkpoint, it will re-enable any *disable_reuse or *hide_reuse options that the player may have used after saving the checkpoint.)

## Subroutines with *gosub and *gosub_scene
 Instead of the *goto command, you can use the *gosub command to go to a label, and then use the *return command to jump back to the line where you called *gosub.
```
  *choice
    #Happy.
      You're happy!
      *gosub saying
      Hopefully, you'll be happy for a very long time!
      *finish
    #Sad.
      You're sad.
      *gosub saying
      Maybe you'll be happier soon!
      *finish
  *label saying
  This, too, shall pass.
  *return

```

If you choose “Happy,” the game will write:

You’re happy! This, too, shall pass. Hopefully, you’ll be happy for a very long time!

It’s great for snippets of code that you would have copied and pasted all over the place.

“Subroutines” are tiny sub-programs that you run in the middle of your program. *gosub is so-called because it activates a subroutine. It is possible to nest subroutines, by using *gosub twice or more before using *return command.

```
  Start One,
  *gosub two
  End One.
  *finish

  *label two
  Start Two,
  *gosub three
  End Two.
  *return

  *label three
  Three.
  *return
```

That code would display:

Start One, Start Two, Three. End Two. End One.

You can also use *gosub_scene to visit another scene file and then *return to the point where you left off. Like *goto_scene, you can also use *gosub_scene to visit a specific label in another file and then *return from it when you’re finished.

```
  *gosub_scene invitations cordial
```

WARNING: Generally speaking, the simpler your ChoiceScript is, the better. It’s possible to abuse *gosub and *gosub_scene to create extremely complex programs. This is rarely a good idea; complex games aren’t any more fun than simple games, but complex games are a lot harder to make. If you think you need a lot of subroutines, consider whether your game might be better if it were simpler.

## Next: Customizing the ChoiceScript Stats Screen

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
