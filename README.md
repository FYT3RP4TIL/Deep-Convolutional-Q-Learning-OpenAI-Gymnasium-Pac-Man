# Deep-Convolutional-Q-Learning-Pac-Man
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
| ```[0, ..., 7]``` | ```0``` | ```[0, 1]``` | ```0``` |


## Version History
A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the “ALE” namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release

## DCQL :
* The inputs were vectors encoded values defining the states of the environment. But
since an encoded vector doesn’t preserve the spatial structure of an image, this is not the best form to
describe a state. 

* The spatial structure is indeed important because it gives us more information to predict
the next state, and predicting the next state is of course essential for our AI to know what is the right next
move. Therefore we need to preserve the spatial structure and to do that, our inputs must be 3D images (2D
for the array of pixels plus one additional dimension for the colors). 

* In that case, the inputs are simply the images of the screen itself, exactly like what a human sees when playing the game. Following this analogy,
the AI acts like a human: it observes the input images of the screen when playing the game, the input images go into a convolutional neural network (the brain for a human) which will detect the state in each image.

* Note :  This convolutional neural network doesn’t contain pooling layers, because they would loose the
location of the objects inside the image, and of course the AI need to keep track of the objects. Therefore
we only keep the convolutional layers, and then by flattening them into a 1-dimensional vector, we get the
input of our previous Deep Q-Learning network.

* Then the same process is being ran.Therefore in summary, Deep Convolutional Q-Learning is the same as Deep Q-Learning, with the only
  difference that the inputs are now images, and a Convolutional Neural Network is added at the beginning
  of the fully-connected Deep Q-Learning network to detect the states (or simply the objects) of the images.

  ![DCQL](https://github.com/FYT3RP4TIL/Deep-Convolutional-Q-Learning-OpenAI-Gymnasium-Pac-Man/assets/113416452/3e13d5d4-fcad-4723-9890-4062f6f988ee)

### Eligibility Trace ( n-Step Q Learning )


* Eligibility traces are one of the basic mechanisms of reinforcement learning. For example,
  in the popular TD(λ) algorithm, the λ refers to the use of an eligibility trace. Almost any
  temporal-di↵erence (TD) method, such as Q-learning or Sarsa, can be combined with
  eligibility traces to obtain a more general method that may learn more efficiently. 

* Eligibility traces unify and generalize TD and Monte Carlo methods. When TD
  methods are augmented with eligibility traces, they produce a family of methods spanning
  a spectrum that has Monte Carlo methods at one end (λ = 1) and one-step TD methods at the other (λ = 0). In between are 
  intermediate methods that are often better than either extreme method. Eligibility traces also provide a way of 
  implementing Monte Carlo methods online and on continuing problems without episodes.

  ![Screenshot 2024-01-21 171551](https://github.com/FYT3RP4TIL/Deep-Convolutional-Q-Learning-OpenAI-Gymnasium-Pac-Man/assets/113416452/a8362500-ab34-41d0-9751-55055fe5ba6d)

  ![Screenshot 2024-01-21 171614](https://github.com/FYT3RP4TIL/Deep-Convolutional-Q-Learning-OpenAI-Gymnasium-Pac-Man/assets/113416452/28c05345-e263-4c22-b355-c996d012010f)

## AI Playing Pac-Man :
  
https://github.com/FYT3RP4TIL/Deep-Convolutional-Q-Learning-OpenAI-Gymnasium-Pac-Man/assets/113416452/feca2797-a82f-4550-ad2f-4d324a728bce

## References

* https://mitpress.mit.edu/9780262039246/reinforcement-learning/
* https://arxiv.org/pdf/1602.01783.pdf
* https://rubikscode.net/2019/07/22/deep-convolutional-q-learning-with-python-and-tensorflow-2-0/
* https://mitpress.mit.edu/9780262039246/reinforcement-learning/















