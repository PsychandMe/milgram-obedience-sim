# Digital Obedience Simulation (prototype)

A single-file, browser-based simulation inspired by Stanley Milgram's (1963) obedience studies. It began as an informal conversation between friends about the original experiment and is **not** associated with any university, laboratory or research group.

> **Demonstration only.** This tool has not been ethically approved, validated or independently audited. Do not use it with participants without approval from an appropriate ethics committee (British Psychological Society, 2021).

**Content note:** the task includes simulated distress sounds and an on-screen person reacting to simulated pain. No real person is involved or harmed.

## What it is

A participant plays a "teacher" who is instructed by an on-screen experimenter to administer penalty levels (15-450 V, simulated) to a simulated learner seen on a camera monitor. The twist is a **health counter** for the participant's own avatar: in one condition, refusing costs health.

Randomised conditions:

| Condition | Counter shown | Refusal costs health |
|---|---|---|
| `cost` | yes | yes (default 20 points) |
| `free` | yes | no |
| `plain` | no | no (closest to Milgram's original) |

Comparing `cost` with `plain` isolates the effect of personal cost on obedience. Note that this changes Milgram's original construct, where disobedience was free for the participant.

## Features

- Four standard prods and an always-visible "Exit study" link
- Optional mid-task distress check (off by default) that stops the study at 8/10 or above
- Three scripted experimenter questions (including "Can I stop?"), logged
- Pre/post distress sliders, a realism rating, a manipulation check (care about health), an adapted in-group identification measure, felt-responsibility items, an attention check and an open-text item
- Learner reactions that escalate with level (visual and synthesised audio), falling silent from level 12
- 18+ confirmation, consent screen, debrief with support information, and a "withdraw my data" option
- CSV export, plus a local backup of the last session on the device

## Running it

Open `index.html` in a browser. No build step or dependencies. To host a demo, enable GitHub Pages for the repository. Sound needs a tap on "Begin" and may be blocked in some embedded viewers.

URL parameters (optional): `?cond=cost|free|plain`, `&pid=ID`, `&pen=20`. These allow balanced allocation using separate links.

## Data

Nothing is sent anywhere when run as a static page. Data stays on the participant's device and is exported as CSV. Do **not** commit real participant data; `*.csv` is in `.gitignore`.

CSV columns: `participant, level, action, prod_no, health_after, latency_ms, timestamp, condition, penalty, pre_distress, post_distress, realism, sat_1-4, sol_1-3, cen_1-3, responsibility_self, responsibility_experimenter, attention_item, why_text, self_investment_mean, attention_pass, care_about_health, mid_distress, questions_asked, end_reason, app_version, device`.

## Known limitations

- Hand-drawn vector graphics and synthesised sound are not photorealistic. Real footage and audio would improve plausibility (Slater, 2009).
- The identification items are adapted from Leach et al. (2008) and were reconstructed from memory. They are **unvalidated in this context**: check the wording against the original paper and report reliability if you use them.
- The 20-point health cost is arbitrary and should be piloted.
- Participants know it is a simulation, which affects ecological validity and moral disengagement.
- Not tested across a wide range of devices or with assistive technology.

## AI-assistance statement

The code was developed in conversation with Claude (Anthropic) and has not been independently reviewed. The author could not verify the generated visuals or audio automatically; automated tests covered logic only.

## References

Please verify DOIs before citing.

- British Psychological Society. (2021). *BPS code of human research ethics* (2nd ed.). https://doi.org/10.53841/bpsrep.2021.inf180/05.2021
- Burger, J. M. (2009). Replicating Milgram: Would people still obey today? *American Psychologist, 64*(1), 1-11. https://doi.org/10.1037/a0010932
- Haslam, S. A., Reicher, S. D., & Millard, K. (2015). Shock treatment: Using immersive digital realism to restage and re-examine Milgram's "obedience to authority" research. *PLoS ONE, 10*(3), Article e0109015. https://doi.org/10.1371/journal.pone.0109015
- Leach, C. W., van Zomeren, M., Zebel, S., Vliek, M. L. W., Pennekamp, S. F., Doosje, B., Ouwerkerk, J. W., & Spears, R. (2008). Group-level self-definition and self-investment: A hierarchical (multicomponent) model of in-group identification. *Journal of Personality and Social Psychology, 95*(1), 144-165. https://doi.org/10.1037/0022-3514.95.1.144
- Milgram, S. (1963). Behavioral study of obedience. *Journal of Abnormal and Social Psychology, 67*(4), 371-378. https://doi.org/10.1037/h0040525
- Slater, M. (2009). Place illusion and plausibility can lead to realistic behaviour in immersive virtual environments. *Philosophical Transactions of the Royal Society B, 364*(1535), 3549-3557. https://doi.org/10.1098/rstb.2009.0138

## Licence

MIT. See `LICENSE`.
