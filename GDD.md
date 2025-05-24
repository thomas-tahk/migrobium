Game Design Document: Microbial Shift (Working Title)
Version: 0.2
Date: 5/19/2025
Author: (Your Name/Itch.io Handle)
Game Jam: Gamedev.tv Game Jam 2025 (Theme: Tiny World)
1. Game Title
   Migrobium (working title)
2. Logline
   As a tiny microbe, consume to grow and automatically adapt, expanding your perception of a microscopic world until a dramatic shift reveals its true, vaster scale.
3. Theme Interpretation
   The game starts the player in a visually confined "tiny world." Growth expands this immediate perception. The core thematic moment is a "scale shift" where the initial environment is revealed to be an infinitesimally small part of a larger one, emphasizing the nested nature of "tiny worlds."
4. Genre
   2D Top-Down Survival / Automatic Growth
5. Target Audience
   Game jam participants and judges.
   Players enjoying simple survival and growth mechanics.
   Developer (you) for learning and MVP creation.
6. Core Gameplay Loop
   Move: Player controls the microbe (follows mouse). Initial vision is limited.
   Consume: Microbe automatically absorbs "food." This fills the Growth/Hunger meter.
   Survive Hunger: The Growth/Hunger meter constantly depletes. If empty for too long, HP decreases.
   Grow & Adapt (Level Up): When the meter is full:

Player character automatically increases in size.
Player's vision radius expands.
Player automatically gains a small, pre-determined or simply acquired trait/stat boost (e.g., based on consumption milestones or a fixed progression). No gameplay interruption for choice.


Survive Threats: Avoid or overcome hostile microbes/hazards.
Reach Scale Shift: Continue until growth and vision expansion trigger a "scale shift" event, revealing a larger world. This is the jam build's goal.
7. Key Features (MVP for Game Jam)
   Player Microbe Control: Top-down mouse-following.
   Limited Vision System: Player's view of the game world starts small and expands with growth (e.g., using Light2D or a shader).
   Consumable System: At least 1 type of "food" that grants Growth/XP.
   Growth/Hunger Meter:

Fills with food.
Depletes over time.
Triggers HP loss if empty for too long.


Automatic Growth & Adaptation:

On meter full: auto-increase size, auto-expand vision.
Implement 1-2 simple, automatic stat boosts or trait acquisitions (e.g., speed up, or unlock "Trait X" after consuming N of Enemy X).


Basic Enemies: At least 1 type of simple enemy that can damage the player.
"Scale Shift" Event: After significant growth/vision expansion, trigger a camera zoom-out or scene change to reveal a larger environment, ending the jam build.
Basic Health & Game Over: Player has HP. If HP <= 0, game over with a restart option.
8. Controls
   Mouse Movement: Player microbe follows the cursor.
   (Optional/Future): Esc for Pause Menu.
9. Game Flow / Player Experience
   Player starts as a tiny microbe with very limited vision in a small area.
   Player consumes food to fill the Growth/Hunger meter, while it constantly depletes.
   Upon filling the meter, the microbe grows, vision expands, and a small, automatic improvement is gained.
   Enemies pose a threat. Running out of "hunger" energy also poses a threat.
   The cycle continues. The player feels progressively more capable within their initial environment as their vision clears.
   Once vision has expanded to the boundaries of the initial play area, the next growth triggers the "Scale Shift," revealing the larger world and concluding the jam demo.
10. Art Style
    Simple 2D. Player can be a circle/blob. Food as particles. Enemies as distinct shapes/colors.
    Focus on clarity. Use free assets or programmer art.
    Vision effect: A dark overlay with a circular transparent area around the player that grows, or a Light2D effect.
11. Sound Design (Minimalist)
    SFX: Consume, growth event, damage taken, enemy alert (optional).
    Utilize free sound assets.
12. Technology
    Engine: Godot Engine.
    Language: GDScript.
13. Scope & MVP Definition (Crucial for the Jam)
    Must-Haves for Playable Build:

Player microbe moves with mouse.
Limited vision that expands with growth.
Food spawns, can be collected.
Growth/Hunger meter: fills with food, depletes over time, causes HP loss if empty.
On meter full: auto-size increase, vision increase, 1-2 simple auto-applied stat boosts/traits.
1 basic enemy type that damages player.
HP system & Game Over/Restart.
The "Scale Shift" reveal as the game's end state.
Can Be Cut / Post-Jam:

Complex trait absorption systems (stick to very simple for jam).
Multiple enemy types or complex AI.
Many diverse automatic upgrades.
Polished art, music, extensive SFX.
14. Risks & Mitigation
    Risk: Implementing the vision expansion and "Scale Shift" smoothly.

Mitigation: For vision, start with a Light2D node; its texture_scale can be tied to player size/level. For Scale Shift, a simple camera zoom (Camera2D.zoom) triggered at the right moment is the MVP. A scene change is more complex.


Risk: Balancing hunger depletion, food availability, and growth rate.

Mitigation: Start with placeholder values and tweak frequently during playtesting. It doesn't need to be perfect, just playable and allow progression to the Scale Shift within a reasonable time (e.g., 5-7 minutes for the jam).


Risk: Automatic trait system becomes too subtle or unnoticeable.

Mitigation: Ensure clear visual or audio feedback when a trait is gained. Keep the effects noticeable (e.g., a clear speed change).


Risk: Scope creep with the "automatic trait acquisition."

Mitigation: Strongly lean towards the simplest version: e.g., every 2nd level up, speed increases by 10%. Or, after consuming 5 of "Enemy X", a specific, simple, hardcoded trait is unlocked. Avoid dynamic systems for the jam.