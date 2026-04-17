# Opal Data Relationship Mapping: The Beast Knowledge Base

## Overview
This document defines the relational schema between the JSON files provided for "The Beast AI Trainer." Use these rules to join and query data across the knowledge base.

## Entity Relationships

### 1. Calendar to Routine
- **Source:** `beast_calendar.json`
- **Link:** `routine_id` (e.g., "BUILD_CHEST_TRIS")
- **Target:** `routines.json` -> `id`
- **Logic:** Each day in the calendar points to a unique routine definition.

### 2. Routine to Exercise Mapping
- **Source:** `routines.json` -> `rounds` -> `exercises` -> `name`
- **Link:** Exercise Name (e.g., "Dumbbell Chest Press")
- **Target:** `exercise_mapping.json` -> `exercise`
- **Logic:** Each exercise in a routine has metadata (muscles, difficulty) defined in the mapping file.

### 3. Exercise Mapping to Machines
- **Source:** `exercise_mapping.json` -> `primary_machine_id` OR `alternative_machine_id`
- **Link:** Machine ID (e.g., "adjustable_bench")
- **Target:** `gym_machines.json` -> `id`
- **Logic:** This link provides the machine description and the correct `image_path` for the frontend.

### 4. User State to Calendar
- **Source:** `user_state.json` -> `current_day`
- **Link:** Numeric Day (1-84)
- **Target:** `beast_calendar.json` -> `weeks` -> `days` -> `day`
- **Logic:** The `user_state` determines which row of the calendar to execute today.

### 5. Progress Tracking
- **Source:** `routines.json` -> `exercises` -> `name`
- **Link:** Exercise Name
- **Target:** `user_progress.json` -> `max_weights` -> `exercise`
- **Logic:** When displaying an exercise, fetch the latest record from `user_progress` to show the user's personal best (PR).

## Query Patterns for Opal
- **"What is my workout today?"**: 
  1. Read `user_state.current_day`.
  2. Find matching day in `beast_calendar.json`.
  3. Get `routine_id`.
  4. Fetch routine details from `routines.json`.
- **"What machine do I need for this exercise?"**:
  1. Take exercise name from `routines.json`.
  2. Find `primary_machine_id` in `exercise_mapping.json`.
  3. Fetch details from `gym_machines.json`.
