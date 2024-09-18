# lab02-debugging

# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

# Debug Process

### vec to vec2
- Bug: 'vec' : undeclared identifier 'uv2' : syntax error
- Solution: We are supposed to use vec2 to represent 2d vec uv2. Therefore, instead of `vec uv2 = 2.0 * uv - vec2(1.0);`, we use `vec2 uv2 = 2.0 * uv - vec2(1.0);`

### H formula
- Bug:  H *= len * iResolution.x / iResolution.x;
- Solution: Firstly, the formula is useless if we time iResolution.x and devided by it. Secondly, the correct formula should be  H *= len * iResolution.x / iResolution.y;
   
### Ray Cast Input
- Bug: `raycast(uv, dir, eye, ref);`
- Solution: We should use the uv2 instead of uv to do the ray cast, as the uv2 is in the correct range [-1,1]

### March Steps
- Bug: ` for(int i = 0; i < 64; ++i)`
- Solution: We should march enough step to get an clear background

### Reflect
- Bug: `dir = reflect(eye, nor);`
- Solution: We should reflect with the eye but to use the dir from the first march `dir = reflect(dir, nor);`

# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
