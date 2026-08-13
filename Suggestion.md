Selenium Manager telemetry usage Bug Fix

Don’t send telemetry on the first run.
Send telemetry only if we can confirm the cache existed from a previous run.
If get_cache_path() returns None, don’t send telemetry.
If se-metadata.json is missing or unreadable, don’t send telemetry.
After the first run, save a marker so the next run can detect that the cache persisted.
Keep this change fail-closed: if we cannot confirm persistence, send nothing.
Do not change the existing version-discovery TTL for this fix.
Add tests for:
First run → no telemetry
Second run with valid cache → telemetry allowed
Missing cache → no telemetry
Unreadable cache → no telemetry
get_cache_path() == None → no telemetry
Handle the metadata File::open() error instead of using unwrap() to prevent crashes.
 
