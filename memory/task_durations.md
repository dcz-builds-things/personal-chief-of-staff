# Task Duration Calibration

How long recurring task-types ACTUALLY take, so the COS blocks the right amount of time.

**Method:** start from seed defaults; whenever a task is marked Done (or you say
"that took longer/shorter"), the COS updates the learned estimate here. Over time
the learned column replaces the guesses — this is the core of behavior learning.

| Task-type | Default | Learned | Notes |
|---|---|---|---|
| [e.g. Workout incl. travel] | 1.5 h | — | |
| [e.g. Deep-work block] | 2 h | — | |
| [e.g. Coffee chat] | 45 m | — | |
| [e.g. Generic admin item] | 30 m | — | refine per task |

_Last updated: [DATE] (seed defaults — no actuals observed yet)._
