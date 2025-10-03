# Unity-Game-Development
”Rick’s Goal” is an infinite 3D runner game built in Unity 2022.3 LTS, inspired by the frantic style of the Subway Surfer mechanics. The game includes a controller for Rick, to move levels around obstacles while keeping score for each mile traveled in the game.

Link for the Game Demo : https://drive.google.com/drive/folders/1inU0-PtNH7UIgSyBd6ppX6ckSa__JbDT


1 Introduction
”Rick’s Goal” is an infinite 3D runner game built in Unity 2022.3 LTS, inspired by the
frantic style of the Subway Surfer mechanics. The game includes a controller for Rick,
to move levels around obstacles while keeping score for each mile traveled in the game.
This paper covers the experience of having the core gameplay elements of physics-based
motion, collision response, scoring, and the progression of different levels implemented
utilizing Animation and Unity scripting capabilities.
2 Tools and Technologies
The game was developed primarily in Unity 2022.3 LTS for the development platform.
C# was utilized for modeling the scripting functionality of the game utilizing Unity’s

Rigidbody physics for a sense of accurate movement and to provide feedback when colli-
sions occurred. The user-interface (UI) was created using Unity Canvas and TextMeshPro

and, in-game, included dynamic scores that updated. In addition, Unity’s scene manager

API was utilized as the function for changing between levels of the game. All the afore-
mentioned tools and technologies afforded the ability integrate the gameplay mechanic

of the game, the UI components, and the level change progression system as part of the
final outcome.
3 Game Architecture

The game architecture uses connected scripts that each fulfill separate roles. Player-
Movement.cs governs physics-driven movement through forces applied to the player’s

Rigidbody; GameManager.cs is the main controller of the game states for resets, level
completion and scene changes; The score.cs script provides score values from the player’s
Z-position and displays them in real-time via TextMeshPro; Collision detection is the
focus of PlayerCollision.cs to halt movement and trigger game over when contacting an
obstacle; there is an EndTrigger.cs that detects level change, and FollowPlayer.cs that
controls the camera to track the player with fixed positional offsets.
4 Core Mechanics Implementation
4.1 Player Movement
The player is moved with Unity’s Rigidbody. A constant forward force of 2000f moves the
player automatically, while the players movement laterally using 500f forces in response
to A/D key inputs. The parameter (ForceMode.VelocityChange) is used to avoid mass
calculations and make the controls more responsive for the player. The game will reset
if the player’s Y-position drops below -1 which also prevents out of bounds errors.
4.2 Collision System
Obstacles are tagged with the tag ”obstacle” and contain colliders. The PlayerCollision.cs
script uses Unity’s “OnCollisionEnter” method to determine Player’s Collision with the
obstacle’s collider. The script disabled the PlayerMovement component and run the

3

“GameManager.EndGame()” method. This stops the gameplay immediately and reloads
the scene after a 1 second delay.
4.3 Scoring System

The score is generated using the Z position of the player, which provides a direct relation-
ship between distance traveled to points. The score.cs script updates a TextMeshPro UI

element every frame to show the current player score. This is intentionally kept simple
so that calculations are avoided and players will focus on the gameplay.
4.4 Level Progression
Level completion occurs when the player reaches an endpoint with a component called

EndTrigger. This calls the “GameManager.completeLevel()” method and displays a level-
complete UI panel and calls the function “LoadNextLevel()” and increments the scene

index so, if another level can be loaded, it will be loaded. If there are no levels to load
then we logged a debug message ”Game Completed”.
4.5 Camera System

The FollowPlayer.cs script performs the camera following functionality. The script up-
dates the camera’s position to match the player’s position plus a fixed offset to maintain

a third-person perspective that is consistent throughout gameplay.
5 UI Scene Management
The Menu.cs script handles main menu navigation, using “SceneManager.LoadScene()”

to start the game. During gameplay, the score UI updates dynamically, while the level-
complete UI panel is activated via the GameManager. Scene transitions are managed

through Unity’s build settings, ensuring proper indexing of levels.
6 Conclusion
The project “Rick’s Goal” is a proper example of using Unity’s physics engine, C scripting,
and UI systems to create a working endless runner. The key developments are responsive
controls, solid collision detection, and dynamic scoring. And the modular code base will
lend itself to future extension and adheres to industry standard development paradigms.
