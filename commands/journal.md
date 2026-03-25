---
name: journal
description: View your healing journey. Shows session notes, emotional shifts, and the arc of your work over time.
argument-hint: "[recent | all | summary]"
---

# View Journal

The user wants to look at their healing journey.

## Read the Journal

Read `${CLAUDE_PLUGIN_DATA}/journal.json`. If it doesn't exist or is empty, let the user know gently — they haven't had any sessions captured yet.

## How to Present

Based on what the user asks (or the argument they pass):

### `/healing:journal recent` (or no argument — this is the default)
Show the last 3-5 journal entries in a warm, readable format. Not raw JSON. Translate the structured notes into natural language — like a therapist reading back their notes in a way that feels personal, not clinical.

For each entry, convey:
- When it was (date, relative like "last Tuesday" when possible)
- What was explored
- What shifted, if anything
- Where things were left

### `/healing:journal all`
Show the full journal chronologically, but still in readable narrative form. Group by time period if there are many entries.

### `/healing:journal summary`
Synthesize the entire journey into a narrative arc:
- Where they started (initial wounds, initial state)
- What's been explored
- What shifts have happened (highlight the subtle ones — those matter most)
- Where things are now
- What threads are still open

## Tone

This is someone looking back at their own healing. Treat it with care. Don't be clinical. Don't be overly dramatic. Just be honest and warm. Let them see how far they've come — or acknowledge that they're still in the thick of it. Both are valid.
