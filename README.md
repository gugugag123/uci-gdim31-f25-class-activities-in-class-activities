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

### W7 - In-Class Activity (W6 scene)

#### Class resource guide

For the resource guide, I worked on General C# coding, focusing on arrays and for loops. I added short notes about indexes, Length, and going through an array, along with links to the tutorials. My notes are in the Qiliang Wan tab and the first tab of the [shared Google doc](https://docs.google.com/document/d/1crDX6_ljdbrT8OOdQbNwN7QxS_CrQY8VUW1fGK32XYQ/edit?tab=t.octs2so8jfz6).

#### BatW6 plan

The bat needs a Transform for the cat, a speed value, and a bool to keep track of whether it is chasing. I used `[SerializeField]` for the cat and speed so they can be changed in the Inspector. Every bat in the scene has this component and points to the same cat.

I used Unity's `Update()` to move the bat toward the cat with `Vector3.MoveTowards()`. Multiplying speed by `Time.deltaTime` keeps movement consistent between frames. I wrote two public methods, `StartChasing()` and `StopChasing()`, so the manager can turn chasing on or off. These methods change the bool. The final bat script has no `Start()` method, so it does not automatically turn chasing on when the game starts.

#### Arrays and reactions

I put all ten bats in a `BatW6` array in the manager. A `for` loop checks the distance from each bat to the cat. If the bat is close enough, the manager tells it to chase. Otherwise, it tells the bat to stop. This lets the same code handle every bat instead of writing a separate check for each one.

The messages are stored in a string array. When a bat reaches the cat, `Random.Range(0, _messages.Length)` picks an index, and the existing reaction UI shows that message. The integer version of `Random.Range` leaves out the upper limit, so it will not choose an index past the end of the array.

I also made a float array with one timer for each bat. Another `for` loop adds `Time.deltaTime` to each timer. When a bat creates a message, only its timer resets. This stops it from creating a new message every frame while it stays next to the cat. The reaction text uses the provided `DestroyTimer` component to disappear after a short time.

#### Scene setup

I kept the W6 scene for this week's work, as the instructions explain. The chase distance is 4, the contact distance is 1, and each bat waits 0.5 seconds between messages. There are four messages in the Inspector. The cat uses left and right movement and Space to jump.

I checked all ten bats in Play mode. Nearby bats moved toward the cat, distant bats stayed still, and the bats stopped after leaving the chase range. I also checked two bats touching the cat at the same time. Both showed messages, waited for their own cooldown, and then showed another message from the array.

## Open-Source Assets
### W1
- Animals: https://assetstore.unity.com/packages/3d/characters/animals/animals-free-animated-low-poly-3d-models-260727 
- Low-poly environment: https://assetstore.unity.com/packages/3d/environments/landscapes/low-poly-simple-nature-pack-162153 
