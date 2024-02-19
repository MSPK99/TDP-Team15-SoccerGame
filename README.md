# 2D Soccer Game AI Simulation 

Our Team Name :    TAKA

## Table of Contents

- [Overview](#overview)
- [Project Features](#project-features)
  - [Player Roles and Positioning](#player-roles-and-positioning)
  - [Acceleration Zones and Sideband Sprints](#acceleration-zones-and-sideband-sprints)
  - [Defensive Strategies: Clearance Kick](#defensive-strategies-clearance-kick)
  - [Player Behaviors and Decision-Making Logic](#player-behaviors-and-decision-making-logic)
  - [Field of Vision for Players](#field-of-vision-for-players)
  - [GUI for Interactive Control, Weather Conditions Impact](#gui-for-interactive-control-weather-conditions-impact)
  - [Foul and Penalty System with Collision Detection](#foul-and-penalty-system-with-collision-detection)
  - [Immersive Sound Effects and Status Prompts](#immersive-sound-effects-and-status-prompts)
  - [3D Goal Replays](#3d-goal-replays)
- [Methodology and Functioning](#methodology-and-functioning)
  - [Game Mechanics](#game-mechanics)
    - [Game Initialization](#game-initialization)
    - [Player Movement](#player-movement)
    - [Action Decisions](#action-decisions)
    - [Game State Updates](#game-state-updates)
- [External Link for Gameplay](#external-link-for-gameplay)
- [Installation, Setup, and Usage](#installation-setup-and-usage)
  - [Getting Started](#getting-started)
- [Technologies Used](#technologies-used)
- [Acknowledgements](#acknowledgements)
- [License](#license)


## Overview

This project is a comprehensive simulation of a Robocup soccer game, meticulously designed and implemented using MATLAB. This project brings to life a 2D soccer game featuring humanoid robots, with a strong focus on strategy, real-time decision-making, and dynamic gameplay. The simulation incorporates a range of weather conditions, player roles, and game events to enrich the user experience. This provides an exceptional platform for exploring artificial intelligence strategies within the realm of sports simulations.


## Project Features

### Player Roles and Positioning

In our simulation, the team is structured around a four-player setup, with each player assuming a vital role that contributes significantly to the game's dynamics. These roles are Forward (FW), Midfielder (MF), Defender (DF), and Goalkeeper (GK), and their strategic positioning on the field is crucial for the flow and outcome of the match.

- **Forward (FW):** The offensive spearhead, primarily active in the attacking half. The Forward is tasked with ball possession, executing attacking plays, and most importantly, scoring goals. As the team's primary attacker, the Forward plays a pivotal role in the team's offensive strategy.

- **Midfielder (MF):** Serving as the versatile link between the team's offensive and defensive efforts, the Midfielder supports the Forward in attack while also assisting the Defender and Goalkeeper in defensive tasks. Their ability to adapt and cover the field makes them indispensable to the team's cohesion.

- **Defender (DF):** The defensive stalwart positioned in the backcourt, focusing on protecting the goal from opposition attacks. The Defender's primary responsibility is to shield the Goalkeeper, intercepting attacks and clearing the ball to maintain the team's defensive integrity.

- **Goalkeeper (GK):** The last line of defense, with a primary focus on safeguarding the goal area. The Goalkeeper's role is primarily defensive, with limited involvement in offensive play, making critical saves to prevent the opposition from scoring.

The interaction and movement of these players, coupled with their engagement with the ball, significantly enhance the excitement of the match. The strategic positioning and the roles they play are depicted in the diagram below, which illustrates the ideal range of activity for each player on the field. The direction of attack is indicated by the red arrow, highlighting the dynamic nature of the game.


![Screenshot 2024-02-18 232219](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/3beb4cda-6014-4669-bd91-d6798e480635)

*Figure: Ideal player positioning with designated roles in the soccer simulation.*


### Acceleration Zones/Sideband Sprints

A novel feature of our simulation is the introduction of acceleration zones located along the pitch's sides, designed to enable players to execute high-velocity runs akin to those performed by wingers in real-life soccer.

These acceleration zones significantly enhance the gameplay by allowing for rapid speed gains, thereby enabling exciting strategies and dynamic plays. For example, a forward might utilize an acceleration zone for a quick sprint down the flank before delivering a cross pass, setting up a midfielder for a critical goal attempt.

![Screenshot 2024-02-18 232146](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/70fa2149-7432-42e0-8aba-02fb5cd1a757)

*Figure: Acceleration zones highlighted on the soccer field, illustrating their strategic importance for fast-paced plays and breakthroughs.*

### Defensive Strategies: Clearance Kick

The simulation features a strategic defense mechanism known as the clearance kick, executed within blue zones near the goal. When the ball enters these critical areas, defenders are triggered to clear it towards a designated safer area (marked by a star in the diagram).

This defensive maneuver reduces the risk of conceding goals and, when combined with sideband sprints, can initiate rapid counter-attacks. The clearance not only neutralizes the immediate threat but also potentially directs the ball into an acceleration zone, introducing additional strategic depth to the gameplay.

![Screenshot 2024-02-18 232201](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/bf87f217-4e09-4476-b2a6-d1c440a82c16)

*Figure: Blue zones indicating clearance kick areas to avert potential goals.*


### Player Behaviors and Decision-Making Logic

In our simulation, each robot player is imbued with distinct behaviors that reflect their roles on the soccer field, ensuring a dynamic and strategic gameplay experience:

- **Strikers**: Tasked with leading the offensive efforts, strikers are adept at applying pressure on the opposition and readying themselves for counter-attacks. They skillfully balance their offensive duties with defensive responsibilities, particularly around the midfield area.
- **Midfielders**: As the linchpin of the team, midfielders bridge the gap between offense and defense. Their role demands flexibility, as they continuously adjust their positioning in response to the ball's location, facilitating control over the game's tempo and strategy.
- **Defenders**: Defenders adopt a conservative approach, focusing on strategic positioning to intercept potential goal threats while also engaging in possession battles. Their primary goal is to protect their half of the field and prevent scoring opportunities.
- **Goalkeeper**: Confined to the penalty area, the goalkeeper exhibits behaviors tailored to neutralize direct threats. Their positioning and actions are meticulously calculated to respond to the game's evolving dynamics, ensuring the goal is safeguarded against incoming attacks.

The core of our simulation's realism lies in the `MovePlayer` function, which analyzes the current state of play—including the ball's location and each player's role—to determine optimal positions, velocities, and viewing angles. This continuous analysis is further refined by the `UpdatePlayer` function, which integrates interactions with the ball, such as shots and passes, rooted in sophisticated decision-making algorithms.

This intricate logic is visualized in a comprehensive decision-making flowchart, detailing the processes behind each ball carrier's actions, from assessing the field to executing strategic plays.

![Screenshot 2024-02-18 231521](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/5e3e182e-d8f0-4797-8f8f-d991a40f31fd)

*Figure: Decision-Making Flowchart for Ball Carriers*

### Field of Vision for Players

In our Robocup soccer simulation, we've meticulously designed the field of vision for each player to mirror the intricacies of real soccer. A key aspect of a player's in-game strategy hinges on their ability to track the ball, which is central to our simulation's realism. To achieve this, players are equipped with sensors that constantly adjust to maintain a lock on the ball's position.

The sensory range of each player is represented as a 96-degree arc, visualized on the field by a yellow dotted line. This arc effectively simulates a realistic field of vision. Within this arc, the specific focus of each player is indicated by a thin white dotted line, positioned directly in the middle of their sensory range. This ensures that players are perpetually cognizant of the ball's location, enabling them to respond promptly and strategically throughout the match.


![Screenshot 2024-02-18 234025](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/05909df9-da98-4cb2-afed-6b27ccfa7895)

*Figure: This figure showcases the players' visual range and orientation, providing insight into how they perceive and interact with their environment during gameplay.*


### GUI for Interactive Control, Weather Conditions Impact


![Screenshot 2024-02-18 231900](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/6b7b93e8-436a-4203-8893-889e7d7b6bfd)

*Figure: Flowchart for GUI*

The GUI is the heart of our soccer simulation, where strategy meets the screen. It’s all about control at your fingertips. Start by setting your team's formation right in the text box. Got a perfect square of 4 players? The lamp shines green, signaling all systems go. If not, it's a glaring red — a nudge to tweak your lineup. With formations down, hit 'Set formation & Run' and watch the field come alive as the game parameters set the stage.

In-play, the GUI is your command hub. Need a breather? The pause button halts the action. Ready to roll again? Hit resume and the match picks up where you left off. And if you fancy a reset, just one click wipes the slate clean for a new game kickoff.

The simulation keeps pace with a loop that's always ticking, updating everything from player positions to the ball's latest zip across the pitch. And it's smart — a collision might just flash a yellow card, and a second? That's a sub off the bench.

![Screenshot 2024-02-18 183057](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/a68c1845-bfb6-42a4-8275-8d1f425a3c37)

*Figure: GUI Interface*
 
The simulation uniquely accounts for varying weather conditions—sunny, rainy, and snowy—each meticulously modeled to influence the game's physics. These conditions affect ball friction and player performance, introducing a strategic layer of complexity to the gameplay.

![Screenshot 2024-02-18 231007](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/e3c4e845-d6ad-4454-b42a-0c9471f83120)

![Screenshot 2024-02-18 231026](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/aa74dc93-85cb-4c20-91d5-d6354ec1ad31)

![Screenshot 2024-02-18 231042](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/90ef5b07-e2f9-4f68-9180-2f22f2123e21)

*Figure:  Weather Impact( Sunny, Rain, Snow) on Gameplay*



### Foul and Penalty System with Collision Detection

To ensure the integrity of gameplay, our soccer simulation strictly adheres to the rules of soccer, with a keen focus on fair play and the enforcement of fouls. The system closely monitors player interactions to detect collisions, using a distance measurement that is slightly less than twice the radius of a player to determine when a foul has occurred. If players remain in contact for longer than a second, a foul is called, and our system impartially assigns a yellow card to one of the participants. This is clearly communicated to players and spectators alike through both a visual on-screen indicator and a text prompt, such as "#3 get a yellow card!", with the player's team color denoted alongside their number.

Following a foul, the game is momentarily paused to allow recognition of the penalty. A persistent marker representing the yellow card is displayed at the game's interface bottom, indicating the penalized player and their team for the game's duration. Should there be repeat offenses, our simulation implements player substitutions, with notifications clearly displayed on-screen and the substitute player entering the game in place of their cautioned teammate.

![Screenshot 2024-02-18 231611](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/fd84dd16-70e2-4207-8244-b74880257c5d)

![Screenshot 2024-02-18 231645](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/5b821cbb-4ec8-48f0-8fe3-2bfa8e072d81)


*Figure: Illustration of a Yellow Card Issuance and Subsequent Player Substitution*

### Immersive Sound Effects and Status Prompts

The simulation recreates the vibrant atmosphere of a soccer stadium, complete with dynamic sound effects and status prompts that bring the game to life. It actively monitors the state of the game, providing immediate auditory and visual feedback for key events like goals and fouls. Celebratory cheers, referee whistles, and informative on-screen text keep players and spectators alike informed and engaged, detailing the nature of the play, involved player numbers, and any necessary substitutions.

The implementation of these features involved complex data handling and efficient global variable use for sound management, ensuring a seamless and immersive experience. Sound effects are tailored to specific game actions, from goal attempts to the thrill of acceleration zone dashes.

![Screenshot 2024-02-18 232031](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/8251627c-0554-4450-94fc-2df56b47ccf9)

*Figure: Out-of-Bounds Scenario with Status Prompt*

Further enhancing the simulation, we've introduced commentary clips, adding a layer of realism and excitement. Imagine the thrill of hearing iconic commentary as the match progresses, deepening the immersive experience of our Robocup soccer simulation.

### 3D Goal Replays (Nothing flashy)

The thrill of a goal is relived with our 3D goal replay feature, which is built upon a sophisticated Matlab script that calculates and plots the ball's trajectory from its initial state to the moment it hits the net. The system leverages global variables to bring up the necessary initial conditions, including the shooter's number and the ball's position and velocity. With the ball's path calculated for each frame, the replay exhibits the ball's journey into the goal, complete with the shooter's team and number for clarity. This slow-motion replay, with velocity finely tuned during testing, adds an impactful layer of engagement to each goal scored.

![Screenshot 2024-02-18 231958](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/a5a6aab4-bc94-42c4-99aa-ec48811b87ac)

*Figure: Flowchart of the 3D Goal Replay Function*

![Screenshot 2024-02-18 231933](https://github.com/MSPK99/TDP-Team15-SoccerGame/assets/157824384/9b149d12-adb7-4259-bded-1390af560bc1)

*Figure: 3D Replay in action*


## Methodology and Functioning

### Game Mechanics

The Robocup 2D Soccer Simulation is a complex system designed to emulate the nuanced and dynamic essence of soccer. It integrates advanced game mechanics to ensure a realistic and engaging gameplay experience. This section outlines the core mechanics that underpin the simulation, covering game initialization, player movement, action decisions, and game state updates.

#### Game Initialization

The simulation kicks off with a comprehensive initialization phase, setting up the field, players, and ball for the match ahead. This phase includes:

- **Field Setup:** The dimensions and features of the soccer field are established, including goal areas and boundary lines, ensuring a realistic playing environment.
- **Player Initialization:** Using scripts such as `FormationCreater.m` and `InitializePlayers.m`, players are positioned in predetermined formations, each assigned a specific role (e.g., forward, midfielder, defender, goalkeeper) that reflects their responsibilities on the field.
- **Ball Placement:** The `InitializeBall.m` script places the ball at the center of the field or at designated spots for kick-offs, free kicks, or penalty shots, readying it for play.

#### Player Movement

Player movement is a critical aspect of the simulation, governed by algorithms that enable realistic navigation and interaction with the ball. The `MovePlayer.m` script allows players to execute actions like running, dribbling, and repositioning, emulating real-life soccer strategies for offense, defense, and midfield play.

#### Action Decisions

At the core of each player's performance on the field is AI-driven decision-making. Through scripts like `ChoosePlayerToPass.m` and `KickBall.m`, players can:

- Identify the best passing opportunities by assessing teammates' positions relative to opponents.
- Attempt shots on goal when in advantageous positions, using calculated angles and power to enhance scoring potential.
- Implement defensive tactics, including clearance kicks and tackles, to counteract opponent strategies.

#### Game State Updates

The simulation constantly updates the game state to accurately reflect the current situation on the field, including:

- **Scoring:** Goals are recorded and the score updated via the `UpdateScore.m` script, with immediate reflection on the scoreboard.
- **Ball Position:** The `UpdateBallPosition.m` script ensures the ball's location is accurately tracked after kicks, passes, or other interactions.
- **Player Status:** Updates to players' positions and states are handled by `UpdatePlayer.m` and `PlotPlayers.m`, showcasing their latest actions, locations, and interactions in real-time.


## External Link for gameplay:

Just have a glimpse of what we could could accomplish. [play_video](https://www.youtube.com/watch?v=GKPF4zju9BI&ab_channel=%E6%9D%A8%E6%B8%85%E5%AE%87)

## Installation, Setup, and Usage

### Getting Started

1. **Matlab Installation**: First, ensure you have Matlab installed on your system. You can acquire Matlab from the [official website](https://matlab.mathworks.com/).

2. **Repository Download**: Clone or download the repository into a single folder on your system.

3. **Opening the Project**: Launch Matlab and navigate to the folder where you downloaded the project.

4. **Exploring the Code**: Feel free to explore the various script files within the project, each detailing a specific functionality of the game. When you're ready to start the simulation, open `Gui.mlapp`.

5. **Using App Designer**: Opening `Gui.mlapp` launches the App Designer, where you'll find important instructions on setting up player formations and understanding the game rules. Take a moment to familiarize yourself with these before proceeding.

6. **Running the Simulation**: After setting the player formations and selecting the desired weather conditions, you can run the game directly from the App Designer.

7. **Experimentation**: Dive into the simulation and experiment with different weather conditions, formations, and explore the various functionalities provided by the buttons within the GUI.

### Technologies Used

This project is built using **MATLAB** and **App Designer**, leveraging their powerful computational and graphical interface capabilities to create an immersive simulation experience.

### Acknowledgements

Special thanks to DAN for providing the Matlab base essential for our project development. Heartfelt gratitude goes out to our entire TAKA team for their dedication and hard work throughout the project. Your efforts are deeply appreciated.

#### Team TAKA

- 2815755M - [MSPK](https://github.com/MSPK99)
- 2817055Y - [Romy](https://github.com/romyfish)
- 2812610J
- 2815238M
- 2816263Y
- 2816238Z

## License

This project is licensed under the MIT License - for more details, see the [LICENSE.md](LICENSE.md) file.

