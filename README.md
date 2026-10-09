## Daniel Armstrong

I build agent infrastructure, and I run two small businesses on it — a lemonade cart and a
glazed-nut line in Michigan City, Indiana. Agents do the outreach: research venues, draft
and send the emails, place the calls, read the replies, move ~2,000 records through a
state machine. Roughly 900 emails and 120 calls have gone out that way.

Mostly it works. The interesting part is the five times it didn't.

### [agent-send-guard](https://github.com/dandevteam-del/agent-send-guard)

Blast-radius controls for autonomous agents that contact real people. Four layers, 20
tests, and the five costed incidents that produced each one.

The short version: **guard the thing that feels the consequence, not the thing your code
is iterating over.** One gatekeeper received 15 emails across 14 records because my filter
was per-record and a person is not a record — it cost fourteen booked events. A deploy
mirrored my scheduled jobs to a second machine and 31 duplicate emails went out while
every guard worked perfectly, just twice, against two copies of state. And an agent asked
to send a wave wrote its own sender and skipped all of it.

Writing the tests found two more faults in guards that had been running in production for
a month and looked healthy — including a hook that crashed on its own most important code
path and so failed **open**, silently, on exactly the bypass it was built for.

### Elsewhere

**[claude-memory-kit](https://github.com/dandevteam-del/claude-memory-kit)** — persistent
project memory for Claude Code · **[zeus-basic](https://github.com/dandevteam-del/zeus-basic)** —
multi-channel agent platform · RunPod serverless workers for FLUX, SadTalker, LatentSync,
Wav2Lip and OmniAvatar.

Before this: $1M+ in SBA lending originated, 300+ small businesses advised. Marquette
finance, D-I scholar-athlete.
