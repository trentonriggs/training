# Training for ChatGPT

Training is a longitudinal fitness-coaching skill for ChatGPT and Codex. It programs strength, hypertrophy, VO₂-max, and Zone 2 training, tracks performance over time, and adapts each session using verified workout history.

The goal is simple: make useful, sustainable progress without having to design your own programming or remember what you did last time.

## What it does

- Builds an individualized weekly training structure around your goals, schedule, equipment, and limitations
- Programs workouts exercise by exercise with exact load, set, and rep targets
- Uses progressive overload while accounting for exercise order, fatigue, setup, and machine differences
- Tracks meaningful strength, repetition, volume, and cardio milestones
- Adapts when equipment is unavailable, performance changes, or pain occurs
- Supports high-energy, analytical, encouraging, or minimal coaching styles
- Combines strength and hypertrophy work with VO₂-max and Zone 2 training when appropriate
- Maintains continuity across conversations through a canonical Google Sheet

## Requirements

- ChatGPT Desktop, Codex CLI, or another compatible Agent Skills host
- A connected Google Drive/Google Sheets account for persistent workout tracking

Google Sheets is the skill's source of truth. Without access to a compatible tracker, Training can discuss workouts, but it cannot provide the intended longitudinal tracking experience.

## Install on ChatGPT Desktop

1. Download [`training/SKILL.md`](training/SKILL.md).
2. Create this folder on your computer:

   ```text
   ~/.agents/skills/training/
   ```

3. Place the downloaded file here:

   ```text
   ~/.agents/skills/training/SKILL.md
   ```

4. Fully quit and reopen ChatGPT Desktop.
5. Start a new conversation and type `@Training`.

The resulting structure should be:

```text
~/.agents/skills/
└── training/
    └── SKILL.md
```

If the skill does not appear, confirm that the file is named exactly `SKILL.md`, verify that it is inside the `training` folder, and restart the app again.

## Install with Terminal

On macOS or Linux, replace `YOUR_USERNAME` with the GitHub username hosting this repository:

```bash
mkdir -p ~/.agents/skills/training
curl -L https://raw.githubusercontent.com/YOUR_USERNAME/chatgpt-training-skill/main/training/SKILL.md \
  -o ~/.agents/skills/training/SKILL.md
```

Then restart ChatGPT Desktop or Codex.

## Getting started

Invoke the skill and ask it to onboard you:

```text
@Training Set up my training program and persistent workout tracker.
```

Training will ask for the information it needs, including your goals, experience, schedule, available equipment, injuries or limitations, exercise preferences, and preferred coaching style. It will then help establish a five-tab Google Sheets tracker before treating workouts as part of the longitudinal program.

## Example prompts

```text
@Training Build today's workout from my verified history.
```

```text
@Training I have 45 minutes in a hotel gym with dumbbells up to 50 lb. Adapt today's session.
```

```text
@Training Give me the intense bodybuilding-coach personality today.
```

```text
@Training Review my last four weeks and tell me where I am progressing or stalling.
```

During a live workout, report each completed exercise with the exact load, load convention, sets, reps, setup, effort, and any pain or form notes. Training will evaluate the result and give you the next exercise in the same response.

## Data and privacy

Your workout history is stored in the Google Sheet created in or supplied from your own Google Drive. Review the permissions requested by ChatGPT and Google before connecting any account.

## Safety

Training is a fitness-programming tool, not medical care. Do not push through pain. Stop or modify movements that cause pain, and seek qualified medical evaluation for severe, persistent, worsening, or concerning symptoms.

## Skill contents

The entire functional workflow is contained in [`training/SKILL.md`](training/SKILL.md). Additional metadata, icons, scripts, or reference files are not required for this version.

