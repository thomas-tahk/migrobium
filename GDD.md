# Game Design Document: Migrobium

**Version:** 0.3 (Ultra-Scoped for Game Jam MVP)
**Date:** 5/24/2025
**Author:** (Your Name/Itch.io Handle)
**Game Jam:** Gamedev.tv Game Jam 2025 (Theme: Tiny World)

## 1. Game Title
Migrobium

## 2. Logline
As a tiny Migrobium, consume to grow, automatically expanding your size and perception of a microscopic world until you reveal its boundaries and "escape" to signify a vaster scale.

## 3. Theme Interpretation
The game starts the player as a tiny organism in a visually confined "tiny world." Growth expands this immediate perception. The core thematic moment is when the player's vision encompasses their entire starting environment, triggering an "escape" that implies a much larger, unseen world, fulfilling the jam's goal.

## 4. Genre
2D Top-Down Survival / Automatic Growth

## 5. Target Audience
*   Game jam participants and judges.
*   Players enjoying simple survival and growth mechanics.
*   Developer (you) for learning and MVP creation under extreme time constraints.

## 6. Core Gameplay Loop
1.  **Move:** Player controls the Migrobium (follows mouse). Initial vision is limited.
2.  **Consume:** Migrobium automatically absorbs "food." This fills the Growth/Hunger meter.
3.  **Survive Hunger:** The Growth/Hunger meter constantly depletes. If empty for too long, HP decreases.
4.  **Grow & Adapt (Level Up):** When the meter is full:
    *   Player character automatically increases in **size**.
    *   Player's **vision radius expands** (revealing more of the immediate dark surroundings).
    *   (Potentially Scoped Out) Player automatically gains a small, pre-determined or simply randomized stat boost.
5.  **Survive Threats:** Avoid or overcome hostile microbes/hazards.
6.  **Reach "World Boundary" & Trigger End Sequence:** Continue until growth and vision expansion allow the player to see the entirety of their initial confined environment (or after a set number of level-ups). This triggers the game's end sequence.

## 7. Key Features (MVP for Game Jam - "Few Hours" Scope)
1.  **Player Migrobium Control:** Top-down mouse-following.
2.  **Limited Vision System:** Player's view starts small and expands with each level-up (e.g., `Light2D` texture scale increases).
3.  **Consumable System:** 1 type of "food" that grants Growth/XP.
4.  **Growth/Hunger Meter:** Fills with food, depletes over time, triggers HP loss if empty.
5.  **Automatic Growth & Adaptation (Simplified):**
    *   On meter full: auto-increase size, auto-expand vision.
    *   *(Likely Cut for "Few Hours" Scope):* The automatic stat boost. Focus on size/vision first.
6.  **Basic Enemies:** 1 type of simple enemy that can damage the player (e.g., moves randomly or slowly towards player).
7.  **HP & Game Over (Death):** Player has HP. If HP <= 0, display a "Game Over" message and a way to restart.
8.  **"Escape the Micro-World" End Sequence (Simplest Version):**
    *   **Trigger:** When vision radius is large enough to effectively show the pre-defined boundaries of the initial small environment (e.g., vision fills the screen), OR after a fixed number of level-ups (e.g., 3-4) if easier.
    *   **Sequence (Prioritize Option A):**
        *   **Option A (Simplest - Target for "Few Hours"):**
            1.  Freeze player input.
            2.  Instantly switch to a pre-drawn static "larger world" image (e.g., showing the previous play area as a tiny speck on a leaf).
            3.  Display text like "Migrobium has outgrown this tiny world!"
            4.  Fade to a "Thanks for Playing! - [Your Name/Handle]" screen.
        *   **Option B (If Miraculously Time Allows):**
            1.  Freeze player input.
            2.  Quickly zoom the camera out (`Camera2D.zoom` via `Tween` over 1-2 seconds) to reveal the larger context.
            3.  Have the tiny player character automatically move in a straight line towards an edge of this newly revealed larger view and off-screen.
            4.  Fade to black. Display end-game message/credits.

## 8. Controls
*   **Mouse Movement:** Player Migrobium follows the cursor.
*   **R Key (or UI Button):** Restart game after Game Over / End Screen.

## 9. Game Flow / Player Experience
1.  Player starts as a tiny Migrobium, vision very restricted.
2.  Player consumes food to fill the Growth/Hunger meter, while it constantly depletes.
3.  Upon filling the meter, the Migrobium grows in size, and its vision expands, revealing more of the immediate play area.
4.  Basic enemies pose a threat. Running out of "hunger" energy also poses a threat leading to HP loss.
5.  After a few growth stages (e.g., 3-4 levels), the player's vision encompasses their entire starting micro-environment.
6.  This triggers the end sequence: a reveal of the larger world context (ideally via static image for scope) and the Migrobium "escaping" or outgrowing it, followed by an end screen.

## 10. Art Style
*   **Visuals:** Extremely simple 2D. Player Migrobium can be a `Sprite2D` with a circle texture or even a `ColorRect`. Food items can be smaller circles/`ColorRects`. Enemies can be different colored `ColorRects` or simple shapes.
*   **Vision Effect:** A `Light2D` node with its `texture_scale` property increased on level up, or a dark overlay with a growing transparent circle.
*   **End Screen Image:** A very simple pre-drawn static image (e.g., using MS Paint or Godot's drawing tools) for the "larger world" reveal.
*   **Assets:** Primarily programmer art. If free basic shapes are found *instantly*, use them; otherwise, create.

## 11. Sound Design (Likely Cut for "Few Hours" Scope)
*   If time permits (last 10-15 minutes):
    *   SFX: Player consuming food (blip), level up (chime), damage (thud).
*   **Assets:** Source from Freesound.org if attempting. Otherwise, no sound.

## 12. Technology
*   **Engine:** Godot Engine.
*   **Language:** GDScript.

## 13. Scope & MVP Definition (Crucial for "Few Hours" Jam)
**Must-Haves for Playable Build (Bare Minimum):**
*   Player Migrobium moves with mouse.
*   Limited vision that expands with growth (e.g., `Light2D` scale).
*   Food spawns, can be collected to fill a growth meter.
*   Growth meter depletes over time (hunger). HP loss if meter empty for too long.
*   On meter full: auto-size increase for player, vision increase.
*   1 basic enemy type that damages player on collision.
*   HP system & Game Over (from enemy or hunger) with a restart mechanism.
*   End sequence triggered after N levels: static image reveal of "larger world," text, "Thanks for playing" screen with restart.

**Definitely Cut for "Few Hours":**
*   Automatic stat boosts beyond size/vision.
*   Complex enemy AI or multiple enemy types.
*   Polished art or detailed animations.
*   Music, most/all sound effects.
*   Complex UI elements (use basic Godot `Label` and `Button` nodes).
*   Option B for the end sequence unless core loop is done in ~half the allotted time.

## 14. Risks & Mitigation
*   **Risk:** Any feature taking longer than 30-60 minutes.
    *   **Mitigation:** Be prepared to cut the feature or simplify it drastically. Stick to the absolute "Must-Haves."
*   **Risk:** Balancing hunger/growth/enemy difficulty.
    *   **Mitigation:** Use hardcoded, simple values. It doesn't need to be balanced, just functional enough to reach the end sequence in a few minutes of play.
*   **Risk:** End sequence implementation.
    *   **Mitigation:** Default to the static image (Option A). This is just changing visibility of nodes and displaying text.

## 15. Post-Jam Potential (Optional - Not for current scope)
*   More diverse evolutions, actual stat boosts.
*   Complex enemy behaviors, ecosystems.
*   Multiple "biomes" or stages of scale.
*   Polished art, sound, and UI.
