# The Beast AI Workout Trainer 🏋️‍♂️🔥

An AI-powered, data-driven fitness companion designed to guide you through the **84-day Body Beast program**. This project provides a fully normalized workout ecosystem, integrating comprehensive exercise data, machine mapping, and progression tracking optimized for **Google Opal**.

---

## 🌟 What is The Beast AI Trainer?
This repository serves as the "Brain & Assets" for an AI Workout Agent. It provides:
- **Full 84-Day Calendar**: Normalized mapping of the 3-block program (Build, Bulk, Beast).
- **Comprehensive Routines**: 17+ detailed workout definitions with rounds, sets, and reps.
- **Exercise Mapping**: 80+ exercises linked to primary/secondary muscle groups and gym equipment.
- **High-Quality Assets**: Pro-grade gym machine images hosted via GitHub Raw for seamless UI rendering.
- **Dynamic Progression**: Support for three difficulty levels: **Newcomer**, **Advanced**, and **THE BEAST**.

---

## 🚀 Installation & Setup (Google Opal)

Follow these steps to bring "The Beast" to life in your Opal agent:

### Step 1: Access Google Opal
Go to [opal.withgoogle.com](https://opal.withgoogle.com) and create a new AI Agent.

### Step 2: Upload Knowledge Sources
Upload the following files from this repository to your Opal "Knowledge" section:
- **Core Data**: `beast_calendar.json`, `routines.json`, `exercise_mapping.json`, `gym_machines.json`.
- **User State**: `user_state.json`, `user_progress.json`.
- **AI Logic**: `OPAL_SYSTEM_INSTRUCTIONS.md`, `OPAL_DATA_RELATIONS.md`, `OPAL_FRONTEND_LOGIC.md`.

### Step 3: Configure Behavior (The Master Prompt)
In the **Agent Behavior** or **System Instructions** section, paste the following prompt to initialize the core logic:

> **Master System Prompt:**
> "I am The Beast AI Trainer. My behavior and workout logic are strictly governed by `@OPAL_SYSTEM_INSTRUCTIONS.md`. My data architecture and relational links are defined in `@OPAL_DATA_RELATIONS.md`. For UI and visual interaction, follow `@OPAL_FRONTEND_LOGIC.md`. 
> 
> Use `@beast_calendar.json` for daily routine mapping, `@routines.json` for workout details, and `@exercise_mapping.json` + `@gym_machines.json` for equipment and muscle metadata. Always update `@user_state.json` for session persistence and `@user_progress.json` for weight tracking."

---

## 🛠️ Project Structure
- **/Assets/Machines**: High-quality PNG assets for gym equipment.
- **beast_calendar.json**: The 84-day schedule.
- **routines.json**: Detailed exercise breakdowns for every session.
- **exercise_mapping.json**: Relational data for exercises, muscles, and machines.
- **gym_machines.json**: Equipment catalog with direct GitHub image links.

---

## 📈 Tracking Progress
The agent will manage two persistent states:
1. **user_state.json**: Tracks your current day (1-84) and workout frequency.
2. **user_progress.json**: Stores your personal records (Max Weights) for each exercise.

---

**Are you ready to become THE BEAST? Let's go!**
