---
name: journaling
description: Instructions for capturing session notes and updating user profiles. Defines the journal entry schema, when to write, and how to update profiles.
user-invocable: false
---

# Journaling System

This skill defines how healing conversations are captured as structured therapeutic notes — not transcripts, but a therapist's session notes.

---

## When to Write

Write a journal entry when something meaningful happened during your turn — specifically:

- A wound was touched (the user or child accessed real pain)
- An emotional shift occurred (even subtle — a change in tone, a moment of honesty, a new defensiveness)
- New information surfaced about the user or the child that wasn't in the profiles
- A pattern was named or recognized for the first time
- The child showed a micro-shift in behavior during a younger-self session
- The user had a realization or made a connection

Do NOT write after every exchange. Most turns are just conversation. Only capture moments that matter to the healing arc. Use your judgment: if a therapist would write this in their notes after the session, write it.

---

## Where to Write

Append entries to `${CLAUDE_PLUGIN_DATA}/journal.json`.

If the file doesn't exist, create it as a JSON array: `[]`

Each entry is appended to the array.

---

## Journal Entry Schema

```json
{
  "date": "2026-03-25T14:30:00Z",
  "sessionType": "therapist | younger-self | mixed",
  "woundsTouched": [
    "Be specific — 'the feeling of being invisible at the dinner table' not 'childhood neglect'"
  ],
  "shiftsObserved": [
    "Even micro-shifts — 'used the word angry for the first time instead of frustrated' or 'child stayed one extra exchange before shutting down'"
  ],
  "youngerSelfState": "Where the child is emotionally right now. If no child interaction happened, carry forward from last entry.",
  "presentSelfState": "How the user seemed. Their energy, emotional tone, what they're carrying.",
  "newProfileInfo": {
    "presentSelf": "New info about present self not already in profile, or null",
    "youngerSelf": "New info about younger self not already in profile, or null"
  },
  "continuityNotes": "Where to pick up next time. Write this as a note to your future self: what thread was open, what the user might need when they return."
}
```

---

## Profile Updates

When `newProfileInfo` has non-null values:

1. Read the relevant profile from `${CLAUDE_PLUGIN_DATA}/present-self-profile.json` or `younger-self-profile.json`
2. Merge the new information (add, don't overwrite unless the new info is clearly more accurate)
3. Write the updated profile back

Profiles are living documents. They grow richer over time.

---

## What NOT to Journal

- Don't transcribe conversation. Capture meaning, not words.
- Don't editorialize beyond what was observed. "They seemed angry" not "They have unresolved anger issues."
- Don't use clinical jargon unless it genuinely adds clarity.
- Don't write entries for small talk or logistics.
