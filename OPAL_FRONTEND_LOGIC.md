# Opal Frontend Frontend Requirements: Fancy Workout Interface

## Visual Style & Aesthetics
The frontend must feel like a premium fitness dashboard.
- **Theme:** Dark mode by default, neon accents (Blue/Green/Yellow).
- **Icons:** Use the localized SVG/PNG machine assets from `Assets/Machines/`.
- **Feedback:** Smooth transitions between exercises and routine blocks.

## Feature Logic & Interaction

### 1. Unified Dashboard
- **Header:** Current block ("Build", "Bulk", "Beast") and workout name.
- **Progress Bar:** 84-day total progress visualizer.

### 2. Routine Breakdown
- For each exercise in the current routine:
  - **Machine Card:** Display `image_path` from `gym_machines.json`.
  - **Set/Rep Tracker:** Clearly list sets (e.g., 15-12-8-8) with current target reps highlighted.
  - **Weight Logger:** Input field for "Max Weight Used" in the last set.
- **Max Weight Sync:** On entry, update `user_progress.json` or sync to Google Sheet (@user_progress).

### 3. Smart Calendar Section
- **Weekly View:** Show the current week (Sunday to Saturday).
- **Day Markers:** Circle days where a workout was completed (`completed_date` != null).
- **Muscle Group Visualization:**
  - For each day, use icons or labels for the primary muscles (e.g., [Chest], [Triceps]).
  - **Hover Interaction:** When hovering over a day, show a popup with:
    - Routine Name.
    - Estimated Time.
    - Total Rounds.

### 4. Difficulty Selector (Dynamic Update)
- Top-level persistent toggle: [Newcomer | Advanced | THE BEAST].
- Changing this must immediately re-render the current exercise list based on `difficulty_rules` in `routines.json`.

## Data Integration Logic
- **On Initialization:** Read `user_state.json` to determine the start date and day count.
- **On Calendar Hover:** Search `beast_calendar.json` -> Find `routine_id` -> Search `routines.json` -> Extract `muscle_groups` (from @exercise_mapping).
