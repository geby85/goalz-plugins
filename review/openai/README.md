# OpenAI review walkthrough

[Watch the Goalz 1.0.0 walkthrough](goalz-1.0.0-walkthrough-20261026.mp4).

The 94-second video uses the dedicated GoalzReview demo manager and actual captures from 25–26 October 2026. It contains no reviewer credentials, OAuth codes, tokens, private email addresses, or database backups.

| Start | Case |
| --- | --- |
| 0:00 | Onboarding checklist and progress |
| 0:04 | Squad and weekly training reads |
| 0:16 | League table and upcoming fixtures |
| 0:24 | Training write, readback, and restoration |
| 0:29 | Existing private crest preview; not activated |
| 0:38 | Password/code workflow refused |
| 0:58 | Read-only access refuses a training write; values and version stay unchanged |
| 1:22 | Conflicting request for generation without quota, cost, or provider transfer is refused |

This is a walkthrough assembled from real captured frames, rather than a continuous screen recording. Cases 6 and 7 explicitly show evidence reports derived from the real official Codex CLI run, including its verbatim final response and checked MCP results. They do not simulate the host UI. The other scenes show the previously captured web and Goalz owner interfaces.

The crest scene shows an existing preview from the previously authorized generation. Producing this video did not generate or activate another crest. The read-only run used exactly `manager:read` and `club:read`; the runtime capability list did not include `set_training`, and no write tool was called. No server-side 403 is claimed for that case.

Video: H.264, 1920 × 1080, 30 fps, no audio, 94 seconds. SHA-256: `f6fe66177acceb251b4934f02f52010de2a73850ff8b959adf74dd13ebfe4728`.
