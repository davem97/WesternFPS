# WesternFPS

# Steps

**Good camera script to handle parenting with player following parented objects movement and/or rotation**

- B
- C

## Movement possibilities

- Walk, run, and strafe forward, left, and right
- Walk backwards
- Crouch walk and strafe forward, left, backwards, and right
    - Cannot jump while crouched
    - Sliding uncrouches the player and plays the slide animation instead
    - Cannot climb ladders, vault or mantle objects while crouching
- Can slightly and briefly move in either forward/left/right/back direction whilst airborne after jumping
- Cannot jump whilst performing any action such as ladder climbing or mantling
- There will be no mantle areas that require a ceiling check
- Three different fall animations for short, medium, and high falls
- No long slopes to slide down on
- There will be several objects where crouching is required to pass through
    - Objects to crouch under will be cube-type only and not round or uneven

## Ladder system
- Can only climb a ladder while facing it and centred
- Camera freelook with horizontal clamp limit while on a ladder
- When exiting a ladder, player body smoothly rotates towards new camera rotation

## Mantle system
- Can only mantle an object while facing it, do not have to be centred
    - Could potentially snap the player rotation towards the object being mantled
- Camera freelook with horizontal clamp limit while on a ladder
- When completing a mantle, player body smoothly rotates towards new camera rotation

## Stuck on edges solution considerations
- Check for colliders around the player that prevent sliding to occur and then cancel it
    - Potentially use the hit from the SphereCast to do this, either prior or during the slide
- Potentially find a better way to handle falling automatically when getting stuck on the edge of an object
- Play the “Falling” animation when sliding off the edge of an object, as currently no animation plays

## General movement and Animations
- When jumping but very minimal vertical movement is occurring, do not play the jump animation
- When running forward against an object and moving a very small amount, play the walk animation
- Consider syncing movement animations with actual movement

## General movement and Camera bugs
- When moving against a collider and jumping, the player will jump forward very far
    - The player should jump very forward very slightly
    - This is most likely due to either the “Mantle” script or “Falling off Edges” code
- When jumping or performing certain animations very close to mesh, the camera will clip into it

## Crouching
- L
- A

## Weapon
- During hipfire shooting, bullet origin direction are sometimes fired ahead of where they should be which is around the crosshair.
    - This does not happen on the same gun repeatedly
    - On each instance of the game, different guns are affected, but not all

## Weapon animations
- While aiming and simultaneously attempting to switch weapons, the new weapon will be zoomed in with the default idle animation playing
    - The correct animation that should be playing is “Aiming”
- Reset FOV when changing weapons but not actively aiming

