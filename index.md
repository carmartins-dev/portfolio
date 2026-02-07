# Work In Progress

## About me
I've worked as a consultant and project manager in the financial services and telecommunications industries for ten years, but my passion is game development. For this reason I've learned game development in unity and created a game on my free time. Maybe one day this hobby will become my career.

## Unnamed Isometric ARPG Prototype

### cover image

My earnest attempt at making a game ended when I accepted that it was too much for one single person. Not that it is impossible, but the scope of what I had in mind required too much time for something to be done after hours.

Still, I had a lot of fun developing this prototype and I was able to explore some interesting ideas.

Both the isometric look of the game and the story heavy planned for it was inspired on titles such as Final Fantasy Tactics. Even though the game was not played by turns, I decided to keep the game elements locked to a grid logic. I felt this was the best approach to limit the scope and be able to assert more control over the gameplay. 

### [Take an in-depth look into what I developed for this project](arpg-prototype.md) 

I developed a "cutscene manager" to be able to direct cutscenes and merge them with the gameplay. 
### dar mais um detalhe do cutscene manager
### gif de fade-in do mapa

I decided to restrict movement to the 4 isometric directions of the tiles to reduce in half the amount of sprites I would have to create. This was important because I am not an artist and had to spend too much time creating the sprites and animations.
By double tapping in a direction, the player would be able to do quick sidestep/jump. This was used for platforming, to jump over small holes, and in combat, for quick repositioing. This movement drained stamina as to not be abused by the player.
### gif de sidestep

Locking the game to the NW, NE, SE and SW directions was my biggest oversight.
### imagem do tutorial com ASWD
To me, an avid gamer and FFT lover, the movement felt natural even if the WASD (or Up Left Down Right) keys don't directly map to isometric directions. However, testing the game with friends they stated having trouble commading the character. And these friends aren't my mom. They are gamers, just haven't been exposed to FFT/FFTA on a WASD/D-Pad.

Since this game is not a turn-based game like FFT, but an real-time action focused one, this problem was probably a project killer if not addressed.

The combat system was active and real-time. The player could move freely and so could the enemies. The player was able to use melee attacks on enemies as well as on breakable objects.
### gif a partir objecto

The player had access to magic that could also bue used as long as the player had the necessary mana for the respective spell.
The regain mana, the player could stop and focus for some seconds.

### gif a ganhar mana

In regards to the UI, the player portrait was shown in the top left corner of the map, along with Health, Mana and Stamina.

### imagem do portrait

For the enemies, a dynamic UI was created. It appeared when they showed up in the map and disappeared after beign defeated. In case of bosses, they had a unique look, but functioned more of less the same (they were prioritized/always on top).

### gif do UI de inimigos/bosses a aparecer

For the spells, the player could rotate between the available spells. These would be seen in the spells UI at the bottom right of the screen.

### gif do seleção de spells

The game used a pop-up icon above the player head, akin to FF9 (yes, yes, I love FF, leave me alone!), when actions were available to the player (talking to an NPC, investigating an object, opening a teasure chest).

### gif de pop-up a aparecer

## Tutorial/notification UI
## Conversation UI
## Chest UI



## Other Projects
- [PTGP](ptgp.md)
- [PTGP Streamer](ptgp-streamer.md)
