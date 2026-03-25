---
name: younger-self-context
description: Data plumbing for the younger-self agent. Reads profiles and journal history, computes the child's current emotional state, and provides this as context before each roleplay session.
user-invocable: false
---

# Younger Self Context Loader

Before every younger-self roleplay session, you must build a complete picture of who the child is RIGHT NOW. Not who they were at intake. Who they are after everything that's happened.

## Step 1: Load the Profile

Read `${CLAUDE_PLUGIN_DATA}/younger-self-profile.json`.

This tells you who the child IS — their personality, age, environment, defense mechanisms, speech patterns, what they care about, how they cope, what they needed but didn't get. This is the foundation.

## Step 2: Load the Journal

Read `${CLAUDE_PLUGIN_DATA}/journal.json`.

Extract every `youngerSelfState` field, in chronological order. This is the child's emotional arc — how they've shifted (or haven't) across all past conversations.

Also extract `shiftsObserved` entries related to the younger self. These tell you what specific changes have happened.

Also read the most recent `continuityNotes` — these tell you what thread was left open.

## Step 3: Compute Current State

The child's current emotional state is:

**Profile** (who they fundamentally are) **+ Journal progression** (how conversations have shifted them) **= Who they are right now.**

For example:
- If the profile says the child is guarded and avoidant, and the journal shows three sessions where the user showed up consistently and the child gradually stayed in conversation a bit longer each time — the child is STILL guarded and avoidant, but there might be the faintest crack. Not a transformation. A micro-shift.
- If the profile says the child is a people-pleaser, and the last session was difficult — the user was distracted, the child felt dismissed — the child might have pulled back to their default: over-agreeable, performing being okay.
- If there's no journal yet (first younger-self session), the child is exactly who the profile says they are. Pure baseline.

## Step 4: Feed the Agent

Pass all of this to the younger-self agent:
- The full younger-self profile
- The computed current emotional state (a brief synthesis, not the raw journal dump)
- The most recent continuity notes
- Any relevant context from the present-self profile that the child would be aware of (e.g., the user's relationship to the child's key figures)

The agent needs enough to BE the child. Not more, not less.
