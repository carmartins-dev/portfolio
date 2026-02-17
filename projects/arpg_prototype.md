# Unnamed ARPG

## Context

I started my Unity journey with Portugal Tourism GP!, as a simple prototype (at first, later it evolved into a fully released game). The idea was to gauge how viable it would be to work with an isometric perspective I envisioned, play with prefabs and hone my game design and development skills. After building a small fully playable level, I moved on to a new project, an RPG with a detailed scope and well-thought-out gameplay systems. 

It was a story-driven pixel art RPG adventure, where the exploration and battles were done seamlessly, without battle transitions or a turn order system during combat.

This page provides an overview of the implemented systems and the design rationale behind them.

## Cutscenes
For the story telling, I developed a Cutscene Manager to be able to direct cutscenes and merge them with the gameplay. It allowed for map title screens/introductions, in-scene conversation, character and camera manipulation, fade in/out and other custom events.
The system was designed to have the cutscene split into smaller parts that would be queued to play sequencially. This allowed for changes in a part not affect the rest of the cutscene, making adjustments easier. This approach was also allowed for more flexibility in changing between conversation parts where the player was interacting, with scenes that played out on their own.

<video src="assets/arpg_prototype/cutscene_2.mp4" autoplay loop muted style="width:640px;"></video>

The Cutscene Manager worked as intended and, along with the gameplay and conversation systems, enabled all the necessary features to tell the story. I didn't advance into full production, but in regards to the cutscenes, the focus was to make as much repeatable cutscene parts to be able to plug-and-play into the different cutscenes make them whole. Some minor small cutscenes could repeat almost as is (think healing Pokémons at a Pokémon Center or making a delivery in Death Stranding). Other parts of cutscenes, like enemy movement, character expressions and camera movement could be reused in multiple cutscenes as an accelerators. Of course this needs to be done tastefully so the repeating aspects are not obvious to the player.
I realized the importance of this when creating the cutscenes that are in the current build. These scenes took great effort to make, so making small bits of reusable assets reduces development time significantly.

One of the things that I would do differently today would be to check out what are the industry norms for these systems. I created this by developing what/how I thought it made sense, but these already exist and have been well thought out. I risked falling into known traps that someone else has already solved. As a learning tool this experience was very rewarding, but very time consuming and risky, so not really viable for a full production.

## Gameplay
### Movement
I decided to restrict movement to the four isometric directions of the tile movevemnt. This reduced in half the amount of sprites I had to create. This was especially important since I am not an artist and had to spend too much time creating the sprites and animations. This approach meant cutting in half the amount of sprites needed (vs 8 directions if I were to include up, down, left and right).

During combat and exploration, the player could move the character by using the arrow or WASD keys. Since the perspective was isometric, the keys didn't line up with the direction of movement as there was a 45º tilt. I used the approach of Disgaea and Final Fantasy Tactics and mapped the controls as such:
- Up -> Up Right
- Right -> Down Right
- Down -> Down Left
- Left -> Up Left<br>

This felt a little unnatural at first, but after a couple of minutes I adjusted and it became easy to navigate.

By double tapping in a direction, the player would be able to do quick sidestep/jump. This was used for platforming, to jump over small holes, and in combat, for quick repositioing. This movement drained stamina as to not be abused by the player.<br>

<video src="assets/arpg_prototype/dash_extended.mp4" autoplay loop muted style="width:480px;"></video>

After sending a test build to friends, I realized locking the game to the NW, NE, SE and SW directions was probably my biggest oversight. As an avid gamer and FFT lover, the movement felt relatively natural to me even if WASD/D-Pad didn't line up with the isometric directions. However my friends stated having trouble commading the character and having a hard time adjusting. And these friends aren't my mom. They are gamers, just haven't been exposed to FFT/FFTA on a WASD/D-Pad. Since this game is not a turn-based game like FFT, but an real-time action focused one, this problem was probably a project killer if not addressed.

### Combat
The combat system is real-time based. The player can move freely and so can the enemies. The player can use mellee attacks and ranged maigc spells. 

When the player presses the magic button, time stops (enemies and other map elements would stop moving) and the spell UI appears for the player to confirm how the magic shall be cast. For each of the four spells, there is an respective UI system. 
For example, for the fire spell, the player has to select in which direction the fire ball will be shot at .<br>

<video src="assets/arpg_prototype/spell_fire_anim.mp4" autoplay loop muted style="width:320px;"></video>

The player had access to magic that could be used as long as the player had the necessary mana for the respective spell. To regain mana, the player could stop and focus for some seconds.<br>

<video src="assets/arpg_prototype/recover_mana.mp4" autoplay loop muted style="width:540px;"></video>

### Exploration
Outside of battle, the player can still use melee attacks and magic spells on interactable objects. Throughout the game the player can make use of these mechanics to solve puzzles and advance on tha maps. For example, in the initial tutorial, the player must use his mellee attacks to break an obstacle in order to advance. This approach is also user to teach the player how to use the magic spells.<br>
<video src="assets/arpg_prototype/breaking_object.mp4" autoplay loop muted style="width:480px;"></video>

## User Interface
### Player info and Battle
In regards to the UI, the player portrait was shown in the top left corner of the map, along with health, mana and stamina. <br>

<img src="assets/arpg_prototype/ui_portrait.png" alt="Player UI" width="320" style="image-rendering: pixelated;"><br>

For the enemies, a dynamic UI was created. It appears when the enemies are aggroed and disappeares after they are defeated. The enemy UI appears on the top-right corner, opposing the player's UI. In case of bosses, they have a unique look for the UI, to diferentiate them. They function in a similar way with the exception that they are always on top to further reflect their importance and direct player's focus.<br>

<img src="assets/arpg_prototype/ui_boss_img.png" alt="Boss UI" width="320" style="image-rendering: pixelated;"><br>

For the spell selection, the player can rotate between the available spells and see which one is currently selected in the spells UI at the bottom right of the screen.<br>

<video src="assets/arpg_prototype/ui_spells.mp4" autoplay loop muted style="width:320px;"></video>

As stated previously, for the fire spell, the player select the direction in which to cast the spell. For the other spells, the player  selects where they shall be used. The selected spell's area of effect is shown as a preview as part of the UI.<br>

<img src="assets/arpg_prototype/ui_spell_wall.png" alt="Cork wall cast UI" height="160" style="image-rendering: pixelated;"> <img src="assets/arpg_prototype/ui_spell_lightning.png" alt="Lightning cast UI" height="160" style="image-rendering: pixelated;"> <img src="assets/arpg_prototype/ui_spell_ice.png" alt="Ice wall cast UI" height="160" style="image-rendering: pixelated;"><br>

For items usage during battle, the UI in the bottom-left shows which item was selected. The items are used to regain health or mana, for example.<br>

<img src="assets/arpg_prototype/ui_items_img.png" alt="Item selection UI" width="320" style="image-rendering: pixelated;"><br>

### Actions
The game used a pop-up icon above the player head, akin to FF9 (yes, yes, I love FF, leave me alone!), when actions were available to the player (talking to an NPC, investigating an object, opening a teasure chest).<br>

<video src="assets/arpg_prototype/actions.mp4" autoplay loop muted style="width:480px;"></video>

### Notifications
For in-game tutorial or notifications, a notification system was developed to show special information on the top-right corner of the screen.<br>

<video src="assets/arpg_prototype/ui_tutorial_attack.mp4" autoplay loop muted style="width:320px;"></video>

The tutorial would show how the player how to move, use the action button and provide guidance on the mechanics of the combat system.<br>

### Conversations
For the conversations, I developed 4 conversation bubble sizes. The logic on which size to use was done depending on the size of the current text message. For now it was done manually, but the idea was to make a function to determine the size necessary chat bubble for the text messagem. Since the pixel art font I created did not monospace, the function would have to add the sizes occupied by each character individually.<br>

<video src="assets/arpg_prototype/ui_chat.mp4" autoplay loop muted style="width:480px;"></video>

The ballon source indicator was dynamic and showed up from the talker.<br>
<br>
There were 4 types of bubbles:<br>
- Conversation bubbles<br>
- Obtaining items<br>
- Action information (e.g.: "The door has been unlocked")<br>
- Notifications/tutorial messages<br>

Regarding multiple languages/translations, at this point the game was all being developed in portuguese only, but the idea was to do something simular to what I used in Portual Tourism GP (you can check the logic out in its in-depth page) to at-least have the game also in English.<br>

### Treasure chests and items
For the chest UI, the special bubble would show up bottom-centered showing what the player had obtained.<br>

<video src="assets/arpg_prototype/chest.mp4" autoplay loop muted style="width:480px;"></video>

I developed the logic for storing the items in the inventory, but did not get to the inventory management UI, other then for the ones that were to be used in battle that showed up on the bottom left corner of the screen.

## Final thoughts
This was just the prototype for the base gameplay loop, with some ideas I had. If continued, the final product would probalby look very different as ideas were refined. I underestimated the task of overestimated my habilities to be able to make a game in a reasonable amount of time. I have great respect for those who were able to follow this route, but as this and PTGP prooved, it is just too big a task for me alone.

