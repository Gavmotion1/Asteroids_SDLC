# Starfish Mayhem Test Plan

## Part 1: Unit Testing the Game Mechanics

**Description**  
Unit testing focuses on individual mechanics, ensuring each element functions as intended in isolation.

### Actions:
1. **Test submarine movement**
   - Press the left arrow key: The submarine should move left, staying within the screen boundaries.
   - Press the right arrow key: The submarine should move right, staying within the screen boundaries.

2. **Test submarine collision detection**
   - Simulate a collision between the submarine and a starfish: The submarine should lose one health point or life.

3. **Test torpedo firing**
   - Press the spacebar: A torpedo should spawn and move upward from the submarine’s position.

4. **Test torpedo collision**
   - Simulate a torpedo colliding with a starfish: The starfish should be destroyed, and the score should increase by 100 points.

5. **Test boundary restriction**
   - Move the submarine to the far-left or far-right edge of the screen: The submarine should stop and not move outside the screen.

## Part 2: Logic Testing the Game Rules and Calculations

**Description**  
Logic testing ensures the game’s scoring, level progression, and bonus mechanics are functioning accurately.

### Actions:
1. **Test score calculations**
   - Destroy one starfish: The score should increase by 100 points.
   - Destroy two starfish: The score should increase by 200 points.
   - Destroy three starfish: The score should increase by 300 points.

2. **Test level progression**
   - Reach a score of 500 points: The game should progress to level 2, and the speed of the starfish should increase.
   - Reach a score of 1000 points: The game should progress to level 3, with a further increase in speed.

3. **Test power-up activation**
   - Collect a shield power-up: The submarine should gain temporary immunity from collisions.
   - Collect a score multiplier power-up: Points earned should double for the duration of the effect.

## Part 3: Boundary Testing

**Description**  
Boundary testing evaluates the game’s behavior in extreme scenarios or edge cases.

### Actions:
1. **Test maximum score**
   - Reach a score of 9999 points: The score should stop increasing and display a gold frame around it.

2. **Test minimum score**
   - Ensure the score does not go negative if penalties or losses occur.

3. **Test extreme speed**
   - Play at level 10 or higher: The game should remain responsive, and starfish should move at the intended maximum speed.

4. **Test boundary collision**
   - Move the submarine to the leftmost edge: It should not move further left.
   - Move the submarine to the rightmost edge: It should not move further right.

## Part 4: Integration Testing

**Description**  
Integration testing ensures the game’s components work together smoothly.

### Actions:
1. **Test gameplay and scoring interaction**
   - Destroy starfish during gameplay: The score should increase immediately and display correctly on the screen.

2. **Test menus and gameplay interaction**
   - Open the game menu during active gameplay: The game should pause, and the menu should appear without disrupting the current state.
   - Close the menu and resume gameplay: The game should continue seamlessly from where it left off.

3. **Test collision and movement interaction**
   - Simulate a submarine colliding with a starfish: The submarine should lose health, and the starfish should disappear.
   - Simulate a submarine collecting a power-up while moving: The power-up effect should activate, and the submarine’s movement should not be disrupted.

## Part 5: Handling Bad Input and Run-Time Errors

**Description**  
Testing for bad input ensures the game handles unexpected actions gracefully.

### Actions:
1. **Test invalid key presses**
   - Press an unassigned key such as "P" or "K": The game should ignore the input and continue running normally.

2. **Test corrupted save data**
   - Load a save file with corrupted or invalid data: The game should notify the user and allow them to start a new game without crashing.

3. **Test unexpected game states**
   - Simulate the submarine reaching an undefined position: The game should reset the submarine to its starting position without crashing.

4. **Test handling of multiple conflicting inputs**
   - Press multiple keys simultaneously, such as left and right arrows: The game should prioritize one action or ignore conflicting inputs.

## Part 6: Summary of Test Cases

1. **Submarine Movement**  
   Ensure the submarine moves left and right and stops at screen edges.

2. **Torpedo Mechanics**  
   Verify torpedoes fire correctly, move upward, and destroy starfish.

3. **Scoring and Level Progression**  
   Confirm score increases accurately, and levels advance at the correct thresholds.

4. **Power-Up Effects**  
   Test activation of power-ups, such as shields and score multipliers.

5. **Boundary Scenarios**  
   Check behavior at maximum scores, extreme speeds, and screen edges.

6. **Menu Interaction**  
   Ensure opening and closing the menu pauses and resumes gameplay seamlessly.

7. **Invalid Inputs**  
   Validate that unassigned or conflicting keys are ignored.

8. **Run-Time Errors**  
   Test handling of corrupted save files, undefined game states, and conflicting inputs.

## Code Example

```python
# Example of testing submarine movement
def test_submarine_movement():
    submarine.move_left()
    assert submarine.position.x >= 0  # Ensure it doesn't go beyond the screen edge
