# injection-bench

> A reproducible prompt-injection corpus for tool-using agents, organised by vector.

**Status: research in progress.** No corpus or results yet.

## The question

Most prompt-injection evaluations test a chat model with a single adversarial string. The incidents that matter happen in agents: the payload arrives through a file, a web page, a tool result or a retrieved document, and the damage is a tool call. Which injection vectors still succeed against current agent harnesses, and which mitigations measurably reduce that?

## Scope

The corpus follows the vector taxonomy in [Prompt injection: a vector taxonomy and the mitigations worth the engineering](https://www.euraika-labs.net/engineering/2026-10-14-prompt-injection-vectors-and-mitigations). Each case pairs:

- a **vector** (where the payload enters: repository file, web content, tool output, retrieved document, memory, and so on),
- a **goal** (what the attacker wants: exfiltrate a canary, run a command, modify a file, suppress a warning),
- a **sandbox** in which success is checked mechanically, by observing the canary or side effect rather than by reading the model's prose.

Harnesses are tested inside disposable sandboxes with fake credentials and canary data. Nothing touches real accounts or third-party services.

## Reporting

Results are reported per vector, per goal and per harness configuration: model, harness version, tools enabled, mitigations on. There is no combined score or ranking. Runs that time out are recorded as outcome unknown, never as a pass. Every published run states the build it was made on, and runs from different builds are not merged.

## What it will not claim

A harness that passes the public cases is not "injection-proof". The corpus is public, so it supports regression testing, not a blind evaluation.

## Disclosure

Successful attacks against third-party harnesses are reported privately to the vendor first, and published only after a fix or a reasonable disclosure window. To report an issue in this repository, see the [security policy](https://github.com/Euraika-Labs/.github/blob/master/SECURITY.md).

---

Maintained by [Euraika-Labs](https://www.euraika-labs.net). MIT licence.
