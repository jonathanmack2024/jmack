# Inbox Triage: take over the schedule

When Jonathan says "Read SETUP.md and do it" in a new session:

1. Check that the Microsoft 365 tools are available (ToolSearch "outlook email search").
   If they are not, stop and tell Jonathan the Microsoft 365 connector isn't on in this session.
2. Use list_triggers to find the existing enabled self-bound inbox triage scheduled task
   (it fires into an older session every 2 hours, CRON_TZ=America/Chicago 38 5-19/2 * * *).
   Disable it with update_trigger (enabled=false). Do not delete it.
3. Create a new scheduled task bound to THIS session (create_trigger, no persistent_session_id,
   no create_new_session_on_fire), name "Jonathan Inbox Triage", same cron
   `CRON_TZ=America/Chicago 38 5-19/2 * * *`, prompt:
   "Run the inbox triage pass: launch one foreground general-purpose subagent with the full
   contents of 'Routine Prompt.md' from this repository as its instructions, then relay its summary."
4. Tell Jonathan in plain words that the schedule moved and when the next run is.

The permission allow rules are in .claude/settings.json. Never send, delete, or forward mail.
