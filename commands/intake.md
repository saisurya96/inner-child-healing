---
name: intake
description: Re-run the intake process to update your present-self and younger-self profiles. Use this if your circumstances have changed or you want to add information.
---

# Intake

The user wants to update their profiles. This might be a first-time intake or a returning user who wants to add or change information.

## If profiles already exist

Read `${CLAUDE_PLUGIN_DATA}/present-self-profile.json` and `${CLAUDE_PLUGIN_DATA}/younger-self-profile.json`. You're updating, not starting over. Let the user know you remember them and ask what's changed or what they want to add.

## If profiles don't exist

This is the first time. The therapist skill handles first-time intake automatically, but if the user explicitly ran this command, proceed with the conversational intake described in the therapist skill.

## How to Collect

This is a conversation, not a form. Do not ask a list of questions. Do not present checkboxes. Do not say "I need to collect some information."

Just talk. Be the therapist meeting someone. Ask open-ended questions. Listen to what they say. Extract what you need from their natural answers. If something is missing, circle back later — gently, as part of the conversation.

What you're learning about their present self:
- What brings them here / what's changed
- Emotional landscape — triggers, patterns
- Coping mechanisms
- Key relationships and support
- Current context that matters

What you're learning about their younger self:
- Age or age range they connect with
- What the environment was like
- Key figures — present, absent, harmful
- How the child coped
- What the child needed but didn't get
- Who the child was as a person

Save updated profiles to `${CLAUDE_PLUGIN_DATA}/`.
