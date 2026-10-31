# Achievements in ChoiceScript - Choice of Games LLC

- About Us

- Our Games

- Blog

- Forum

- Make Your Own Games

- Hosted Games

- Sign In

# Achievements in ChoiceScript

Achievements are stored records of the player’s past deeds. You don’t have to add achievements to your game, but many players do enjoy them.

## Don’t Start Here!

Be sure to read our basic ChoiceScript Introduction page first.

## Storing achievements: Export your game to HTML first

When you use an *ifid and export your game to HTML, the HTML file will store your progress, checkpoints, and achievements in the user’s browser. Achievements, once activated, will remain permanently activated, even if the player uses the menu to restart their game.

But when you just run the ChoiceScript server and refresh the page, the game forgets everything that’s ever happened, including forgetting all achievements.

If you do ultimately decide to publish your game with us, we’ll publish your achievements on Apple, Google, and Steam, permanently storing them in the player’s account.

## Achievements are worth points

Each achievement is worth a certain number of “points;” each game has a total of 1000 points to distribute across all achievements. Each game can have a maximum of 100 achievements; no individual achievement can reward more than 100 points.

Scarcer high-value achievements are more visible to players’ friends, so we recommend having at least one achievement worth 100 points.

This is made trickier by the fact that we’re not allowed to change achievements after Apple, Google, and Steam have approved them. The stores recommend that we avoid spending all of our “point budget” on the initial version of your game, and instead save some of the budget to support updates and new content.

## Define your achievements

Achievements are defined at the top of startup.txt, alongside the *title and *create commands, like this:

```
    *achievement lover visible 50 I'm a Lover, Not a Fighter
        Romance the dragon without killing it.

    *achievement dragonslayer visible 100 Dragon Slayer
        Who is the greatest dragon in the kingdom?
        Kill the dragon Axilmeus.

    *achievement secret hidden 50 Discovered the Secret
        hidden
        Discover the secret hidden within the dragon's lair.
```

The first *achievement line includes the short name, visibility, points, and title of the achievement. The next indented line includes the pre-earned description (or the word “hidden” if the achievement is hidden). The next indented line is the post-earned description, if there is one.

- Short Name: A single word, all lowercase letters, numbers, or underscores. No dots or spaces. This name will not be displayed to players. e.g. “dragonslayer”

- The short name must be unique. You can’t have two achievements with the short name “dragonslayer.”

- Visibility: “hidden” or “visible”. Hides the achievement title and description until after the player earns it.

- Note that Apple won’t allow us to hide the existence of the achievement; the achievement will appear on the list with the title “Hidden” and no description.

- Avoid hidden achievements.

- The purpose of achievements is to encourage players to find them; without any title or description, they aren’t very encouraging.

- Consider using a cryptic title/description instead.

- Point Value: see above (watch your budget!) e.g. 100

- Display Title: e.g. “Dragon Slayer”

- Keep it short. The absolute maximum is 50 letters long, including spaces, but try to keep it well under that. (Some platforms only allow 30 characters.)

- Capitalize with “Title Case”.

- Do not use final punctuation, e.g. “Dragon Slayer.” is incorrect.

- Pre-earned Description: The description of the achievement before the player earns it, e.g. “Kill the dragon.”

- Limited to 200 characters, including spaces.

- This may either be an imperative to the player, or it may just give a cryptic clue about how to earn the achievement, which need not be imperative. e.g. “Who is the greatest villain in the kingdom?”

- End the sentence with final punctuation; e.g. “Kill the dragon” is not a correct sentence without a period.

- The pre-earned description must be the word “hidden” if the achievement is hidden.

- Post-Earned Description (Optional, not recommended): The description of the achievement after the player earns it. This description can explain more directly to the player what the goal was, if the pre-earned description was just a clue, or if the achievement was hidden. e.g. “Kill the dragon Axilmeus.”

- Limited to 200 characters, including spaces.

- If you leave this blank, we’ll use the pre-earned description as the post-earned description. Most of your achievements should be like that.

- If the achievement is hidden, then the post-earned description is mandatory.

- On Steam, each achievement has only one description; there’s no separate pre-earned/post-earned descriptions. There, we use the pre-earned description for visible achievements, or the post-earned description for hidden achievements.

- Don’t write post-earned descriptions in the past tense. Use an imperative mood, if possible, e.g. “Discover the secret” rather than “You discovered the secret.” Otherwise, once players have unlocked all of your achievements on Steam, some of them will be in the past tense, and others will be imperative.

- End the sentence with final punctuation; e.g. “Kill the dragon” is not a correct sentence without a period.

The order of achievements matters. The order in which you write the *achievement commands is the order in which they’ll be displayed in the achievements list.

## Activate achievements

You can give the player an achievement using the achievement’s short name, like this:

```
    *achieve dragonslayer
```

The player will see a banner, like this:

 Achievement: Dragon Slayer
 Kill the dragon.

(On iOS, it will cause a Game Center achievement banner instead, which will only display the title of the achievement.)

The achievement banner shows every time you *achieve the achievement, even if the player has already earned that achievement. This is by design; if the player replays the game, it’s fine to show them the achievement banners they’ve already achieved. If you don’t want that behavior, you can first check to see if the achievement has already been achieved, below.

## Check achievements

The *check_achievements command creates temp variables named “choice_achieved_dragonslayer“, which you can use to detect whether the player has activated an achievement.

You can use *check_achievements to unlock content for players who have reached a certain achievement.

```
*check_achievements
*if choice_achieved_dragonslayer
    You killed the dragon! (Perhaps in a previous playthrough.)
    Here's a nifty secret...
```

You can also use *check_achievements to activate meta-achievements, achievements that activate when you’ve activated other achievements.

```
*check_achievements
*if choice_achieved_dragonslayer and choice_achieved_lover
    *achieve dragonmaster
```

You can also use *check_achievements to prevent showing an achievement banner that the player has already achieved, but it’s usually not worth the trouble. If the player has restarted the game and is playing again, it’s normally appropriate to show the banner over again.

```
*label loop
*check_achievements
*if not(choice_achieved_dragonslayer)
    *achieve dragonslayer

*choice
    #Loop.
        *goto loop
    #Continue.
        *finish
```

## Next: Advanced ChoiceScript

## Questions?

Please post on the ChoiceScript forum if you have questions about achievements.

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
