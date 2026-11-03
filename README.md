# in-class-activities
## Devlogs
### W1
Write your W1 activity Devlog here.

### W2
Create future Devlog sub-headers with the three # symbols, then write your Devlogs below them.

### W6 — In-Class Activity (Week 5 scene)

#### DeerW5 plan

My plan was to give the deer two member variables: a Transform for the target and a NavMeshAgent reference. I used `[SerializeField]` for the target so I could drag an object into the Inspector. A Transform makes sense here because I need the object's position, and I can easily choose a different object later.

I only needed `Start()` for this part. It runs when the game starts, gets the NavMeshAgent with `GetComponent<NavMeshAgent>()`, and tells it where to go with `SetDestination(_target.position)`. The agent takes care of moving along the NavMesh, so I don't need to move the deer myself every frame. I attached the script to the Deer and picked the red mushroom as its target.

#### Cat movement

For the cat, I started with a zero vector in `Update()`. W adds `Vector3.forward`, and S adds `Vector3.back`. Then I use `Translate()` with the move speed and `Time.deltaTime` to move the cat. This way, the movement isn't based on how many frames the computer runs. If both keys are pressed, the two directions cancel each other out.

To flip the controls, I multiply the movement vector by -1 when `_flipWSControls` is checked. That switches W to backward and S to forward. I left it checked in the final scene to show this step. Unchecking it gives the normal controls again. A and D still turn the cat.

## Open-Source Assets
### W1
- Animals: https://assetstore.unity.com/packages/3d/characters/animals/animals-free-animated-low-poly-3d-models-260727 
- Low-poly environment: https://assetstore.unity.com/packages/3d/environments/landscapes/low-poly-simple-nature-pack-162153 
