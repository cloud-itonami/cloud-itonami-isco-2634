# cloud-itonami-isco-2634

Open Occupation Blueprint for **ISCO-08 2634**: Psychologists.

This repository designs a forkable OSS business for an independent licensed psychologist: an intake-support robot performs check-in and intake-form assistance under a governor-gated actor, so the practice keeps its own session and consent records instead of renting a closed EHR/practice-management SaaS.

## Robotics premise

All cloud-itonami verticals are designed on the premise that a **robot performs
the physical domain work**. Here a scheduling and intake-support robot performs waiting-room check-in and intake-form assistance under an actor that proposes
actions and an independent **Psychology Governor** that gates them. The governor never
dispatches hardware itself; `:high`/`:safety-critical` actions (such as
crisis-risk disclosures, or involuntary-hold recommendations) require human sign-off.

A live sample of the operator console (robotics safety console, shared template) is rendered in [docs/samples/operator-console.html](docs/samples/operator-console.html) — pure-data HTML output of `kotoba.robotics.ui`.

## Core Contract

```text
client consent + intake assessment + treatment plan
        |
        v
Practice Advisor -> Psychology Governor -> session/document, or human sign-off
        |
        v
robot actions (gated) + operating records + audit ledger
```

No automated advice can dispatch a robot action the governor refuses, suppress
an operating record, or disclose sensitive data without governor approval and
audit evidence.

## Capability layer

Resolves via [`kotoba-lang/occupation`](https://github.com/kotoba-lang/occupation)
(ISCO-08 `2634`). Required capabilities:

- :robotics
- :identity
- :forms
- :dmn
- :bpmn
- :audit-ledger

See [`docs/business-model.md`](docs/business-model.md) and
[`docs/operator-guide.md`](docs/operator-guide.md).

## License

AGPL-3.0-or-later.
