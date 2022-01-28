---
AUTOGENERATED: DO NOT EDIT FILE DIRECTLY
layout: env
title: Lunar Lander Continuous
grid:
   - Action Space: Box(-1.0, 1.0, (2,), float32)
   - Observation Shape: (8,)
   - Observation High: [inf inf inf inf inf inf inf inf]
   - Observation Low: [-inf -inf -inf -inf -inf -inf -inf -inf]
   - Import: <code>gym.make("LunarLanderContinuous-v2")</code>
---
### Description
This environment is a classic rocket trajectory optimization problem.
According to Pontryagin's maximum principle, it is optimal to fire the
engine at full throttle or turn it off. This is the reason why this
environment has discreet actions: engine on or off.

There are two environment versions: discrete or continuous.
The landing pad is always at coordinates (0,0). The coordinates are the
first two numbers in the state vector.
Landing outside the landing pad is possible. Fuel is infinite, so an agent
can learn to fly and then land on its first attempt.

To see a heuristic landing, run:
```
python gym/envs/box2d/lunar_lander.py
```
<!-- To play yourself, run: -->
<!-- python examples/agents/keyboard_agent.py LunarLander-v2 -->

## Action Space
There are four discrete actions available: do nothing, fire left
orientation engine, fire main engine, fire right orientation engine.

## Observation Space
There are 8 states: the coordinates of the lander in `x` & `y`, its linear
velocities in `x` & `y`, its angle, its angular velocity, and two boleans
showing if each leg is in contact with the ground or not.

## Rewards
Reward for moving from the top of the screen to the landing pad and zero
speed is about 100..140 points.
If the lander moves away from the landing pad it loses reward.
If the lander crashes, it receives an additional -100 points. If it comes
to rest, it receives an additional +100 points. Each leg with ground
contact is +10 points.
Firing the main engine is -0.3 points each frame. Firing the side engine
is -0.03 points each frame. Solved is 200 points.

## Starting State
The lander starts at the top center of the viewport with a random initial
force applied to its center of mass.

## Episode Termination
The episode finishes if:
1) the lander crashes (the lander body gets in contact with the moon);
2) the lander gets outside of the viewport (`x` coordinate is greater than 1);
3) the lander is not awake. From the [Box2D docs](https://box2d.org/documentation/md__d_1__git_hub_box2d_docs_dynamics.html#autotoc_md61),
    a body which is not awake is a body which doesn't move and doesn't
    collide with any other body:
> When Box2D determines that a body (or group of bodies) has come to rest,
> the body enters a sleep state which has very little CPU overhead. If a
> body is awake and collides with a sleeping body, then the sleeping body
> wakes up. Bodies will also wake up if a joint or contact attached to
> them is destroyed.

## Arguments
To use to the _continuous_ environment, you need to specify the
`continuous"=True` argument like below:
```python
import gym
env = gym.make("LunarLander-v2", continuous=True)
```

<!-- ### Version History -->
<!-- - v2: -->
<!-- - v1: -->

<!-- ### References -->

## Credits
Created by Oleg Klimov