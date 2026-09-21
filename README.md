# Training for ChatGPT and Codex

Training is a longitudinal fitness-coaching skill for strength, muscle, VO₂, and aerobic fitness. It builds workouts around your goals, time, equipment, and actual results, then carries useful context forward through a verified Google Sheets record.

## What it does

- Builds a realistic week and today's workout, including warm-up, effort, rest, and a time budget.
- Coaches set by set or gives the full session, according to your request.
- Progresses comparable work without confusing different machines, load conventions, exercise order, or fatigue.
- Adapts for missing equipment, interrupted sessions, plateaus, and changing goals.
- Introduces cardio intervals according to readiness rather than giving every beginner the same protocol.
- Separates planned work, reported work, and verified saved history.
- Reconciles checkpoints and uncertain saves before retrying, preserving manual edits.
- Offers Intense Bodybuilding Coach, Performance Coach, Positive Hype Coach, and Minimal Coach styles.

Google Sheets is the canonical record for ongoing coaching. Without it, Training can still provide a **provisional workout** and a copyable **unsaved log**. It will not claim persistent memory or verified progression from unavailable history.

## Requirements

Use a host that supports Agent Skills, such as ChatGPT or Codex. Available skill installation methods and connectors depend on the host and workspace. A skill supplies instructions; it does not install a Google Sheets or Apple Health connector or grant account access.

For persistent tracking, the host needs authorized access to read and write the selected Google Sheet. Drive search alone is insufficient. Apple Health is optional and is used only when relevant data are actually accessible.

## Install the complete skill

Keep the entire `training/` directory together. Downloading only `SKILL.md` omits the programming and tracking references.

```text
training/
├── SKILL.md
├── agents/openai.yaml
├── assets/icon.svg
└── references/
    ├── programming.md
    └── tracking.md
```

For a new local Codex installation, run from this repository's root:

```bash
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/training" ] || [ -L "$HOME/.agents/skills/training" ]; then
  printf '%s\n' 'Training already exists; review and back it up before updating.'
else
  cp -R training "$HOME/.agents/skills/training"
fi
```

For an existing installation, compare and back up any local customizations, then update the full skill directory. Codex detects skill changes; restart it if the update does not appear. In ChatGPT, use the installation/import method available in your skill interface and include all supporting files. The local path above documents Codex discovery, not a guaranteed installation method for every ChatGPT surface. See [OpenAI's skill installation and authoring guidance](https://learn.chatgpt.com/docs/build-skills).

Invoke it as `@Training` in ChatGPT or `$training` in Codex when it is available in the skill picker. This repository does not install or publish the skill automatically.

## Getting started

```text
@Training Set up my training program and persistent tracker. My priority is
strength, then cardio fitness. I can train three days a week for 45 minutes.
```

Training reuses known context and asks only for missing information that changes the plan. If you already have a tracker, supply its link. The five tabs remain **Profile & Goals**, **Workout Log**, **Weekly Program**, **Progression / PRs**, and **Equipment Library**. Existing log columns and formulas are preserved; new trackers include session/entry identifiers to help reconcile saves.

Other useful prompts:

```text
@Training Build today's workout from my verified history. I have 35 minutes.
@Training I'm at a hotel with dumbbells up to 50 lb. Adapt today's session.
@Training Press: 20 kg per dumbbell, 10/10/9, about two reps left. What's next?
@Training Save a checkpoint; I'll finish later.
@Training Review my last four weeks and explain one change worth making.
@Training No tracker today. Give me a provisional beginner workout.
@Training Tone it down — minimal coach for this session.
```

Report actual sets, reps, units, load convention, effort, and any pain or setup changes. Unknown details remain unknown. At completion, Training reports whether the record is unsaved, checkpoint verified, save unverified, partially verified, or logged and verified. Keep the tracker link and any recovery record for a new conversation; cross-chat continuity depends on accessible history.

## Data and safety

Workout history stays in the workbook you select or authorize Training to create. The skill does not authorize public sharing, unrelated health-data collection, or changes to your account permissions. Review the permissions of your host and connectors.

Training supports general fitness programming, not diagnosis or rehabilitation. Pain changes the plan; possible emergency symptoms stop the session. Coaching intensity never means pushing through concerning symptoms.

## Research and validation

- [Research and design decisions](RESEARCH.md) link the official skill guidance and fitness sources behind this revision.
- [Behavioral evaluation guide and results](evals/README.md) explain the scenarios, checks, evidence, and remaining live-integration tests.
- [Scenario fixtures](evals/scenarios.json) cover coaching, ambiguous results, progression, pain, persistence, corrections, and interruptions.

The skill remains instruction-only: no runtime dependencies, credentials, or executable training scripts are bundled. Repository research and eval files are for maintainers and are not loaded during coaching.
