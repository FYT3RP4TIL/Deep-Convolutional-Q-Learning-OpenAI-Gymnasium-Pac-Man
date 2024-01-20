# Deep-Convolutional-Q-Learning-Pac-Man!
![1](https://github.com/FYT3RP4TIL/Deep-Convolutional-Q-Learning-OpenAI-Gymnasium-Pac-Man/assets/113416452/4beaca2c-f9ac-4c57-95c4-683cfae19fb2)

## Environment :

Pacman
This environment is part of the [Atari environments](https://gymnasium.farama.org/environments/atari/). Please read that page first for general information.
| Action Space | ``` Discrete(5) ``` |
| :---   | :--- | 
| Observation Space |  ``` Box(0, 255, (250, 160, 3), uint8) ``` | 
| Import | ``` gymnasium.make("ALE/Pacman-v5") ``` |


## Description
A classic arcade game. Move Pac Man around a maze collecting food and avoiding ghosts- unless you eat a Power Pellet, then you can eat the ghosts too!

## Actions
Pacman has the action space of ```Discrete(5)``` with the table below listing the meaning of each action’s meanings. To enable all 18 possible actions that can be performed on an Atari 2600, specify ```full_action_space=True``` during initialization or by passing ```full_action_space=True``` if less computational power set ```full_action_space=False``` to ```gymnasium.make```

| Value | Meaning | Value | Meaning | Value | Meaning |
| :---   | :--- | :--- | :--- | :--- | :--- | 
| ```0``` | ```NOOP``` | ```1``` | ```UP``` | ```2``` | ```RIGHT``` |
| ```3``` | ```LEFT``` | ```4``` | ```DOWN``` |

## Observations

Atari environments have three possible observation types: ```"rgb"```, ```"grayscale"``` and ```"ram"```.

* ```obs_type="rgb" -> observation_space=Box(0, 255, (210, 160, 3), np.uint8)```

* ```obs_type="ram" -> observation_space=Box(0, 255, (128,), np.uint8)```

* ```obs_type="grayscale" -> Box(0, 255, (210, 160), np.uint8)```, a grayscale version of the “rgb” type

See variants section for the type of observation used by each environment id by default.

## Variants
Pacman has different variants of the environment id which have differences in observation, the number of frame-skips and the repeat action probability. The variant used :

| Env-id | obs_type= | frameskip= | repeat_action_probability= |
| :---   | :--- | :--- | :--- | 
| MsPacman-ramDeterministic-v0 | ```"ram"``` | ```4``` | ```0.25``` |  

## Difficulty and modes
It is possible to specify various flavors of the environment via the keyword arguments difficulty and mode. A flavor is a combination of a game mode and a difficulty setting. The table below lists the possible difficulty and mode values along with the default values.

Available Modes | Default Mode | Available Difficulties | Default Difficulty |
| :---   | :--- | :--- | :--- | 
| [0, ..., 7] | 0 | [0, 1] | 0 |


## Version History
A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the “ALE” namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release
