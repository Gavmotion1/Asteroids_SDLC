# Initialize game
Initialize game screen (dimensions based on platform, e.g., 800x600)
Initialize player submarine (position, speed, health, and appearance)
Initialize score = 0
Initialize level = 1
Initialize lives = 3
Initialize starfish (enemies) list as empty
Initialize collectible power-ups list as empty
Initialize game speed = normal
Set game state = running

# Input controls
Define controls:
    "Left Arrow" moves submarine left
    "Right Arrow" moves submarine right
    "Space" triggers torpedo to destroy starfish
    "Escape" pauses the game

# Game loop
While game state is running:
    Clear screen
    Display score, level, and lives
    Spawn starfish at random positions at the top of the screen
    Spawn power-ups randomly based on level

    # Update player movement
    If "Left Arrow" is pressed:
        Move submarine left (within screen boundaries)
    If "Right Arrow" is pressed:
        Move submarine right (within screen boundaries)

    # Torpedo logic
    If "Space" is pressed:
        Fire torpedo from submarine position
        For each starfish:
            If torpedo collides with starfish:
                Destroy starfish
                Increase score

    # Starfish movement
    For each starfish:
        Move starfish down the screen based on game speed
        If starfish collides with submarine:
            Reduce player health or lives
            Remove starfish from the screen
        If starfish moves off the bottom of the screen:
            Remove starfish (missed)

    # Power-up logic
    For each power-up:
        Move power-up down the screen
        If submarine collides with power-up:
            Activate power-up effect:
                e.g., increase score multiplier, slow starfish speed, grant temporary shield

    # Level-up logic
    If score exceeds threshold for next level:
        Increase level
        Increase game speed
        Add new starfish types or patterns
        Add additional power-ups

    # Check for game-over condition
    If player health <= 0 or lives <= 0:
        Set game state = game over

    # Update display
    Render submarine, starfish, power-ups, and game status
    Refresh game screen

# End game
If game state is game over:
    Display "Game Over" screen with final score
    Ask player if they want to restart or quit
    If player chooses to restart:
        Reset all variables (score, level, lives, etc.)
        Set game state = running
    If player chooses to quit:
        Exit game

# Clean-up and end game
Release game resources (e.g., memory, assets)
Close game window
End


