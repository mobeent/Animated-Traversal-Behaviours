# Animated-Traversal-Behaviours

Project Video:

When trying to use a software for some reason there was a delay from one waypoint to another due to which I had to capture it by phone.

https://youtu.be/seOfCN_XJEA

Source Code cannot be uploaded as I do not own the base engine that this project works on. Below is the general description of the project. Programming language used is C++ with Directx9, Directx11 and OpenGL. Other Software used is Maya 2017 to position the characters and set up a scene and then transfer it to the engine using Lua scripts

Add animated traversal behaviors, jumping over cover, taking cover, low cover/high cover. Create different kinds of Waypoints where soldier can sync location and play animation. For example waypoint for low cover should be able to specify location where soldier should start playing animation.

* Waypoint is just an point specified in Maya towards which the character has to move, this is not visible in the final rendering
* Updated Scripts for Waypoints to give the name of animation to be played when loaded from Maya i.e now the character knows what animation to play when moving towards that particular waypoint
* Made state machines for the vampire to handle the switch between different animations, this includes behaviorSM, movementSM and animationSM
* BehaviourSM is the encapsulating SM which tells the Vampire character what to do, MovementSM is under the BehaviourSM and handles the movement and lastly the AnimationSM is called to change the animation according to the behaviour.
* Used Animation Driven Motion i.e the movement in the animation was removed and stored seperately and applied to the scene node according to the direction it was supposed to move. This way the speed of the character is determined by the animation rather than hardcoding the values.
* Synchronisation with the waypoints on when to play animation. Details in below points
* For low cover and cover the vampire resumes the motion it was carrying i.e walk or run until it reaches near the waypoint
* If vampire is in cover and needs to run it first plays animation of coming out of low cover or cover and then moves towards the waypoint
* No jump animation was present so implemented jump using the stand_jump, jump_idle and jump to stand animations one after the other and hardcoded the distance from the waypoint when it needs to play
* When in cover if there is no further waypoint it remains in cover. For all others it goes to idle as in SoldierNPC
