# Baseline Notes

Release summaries and notes from `baseline-package.json` inside each ZIP, listed in descending baseline order (newest first).
Baselines with neither a summary nor release notes are marked **Test baseline**. Recorded wording is retained; list formatting is normalized for Markdown.
Package timestamps use Europe/Istanbul time (UTC+03:00).

## Baseline 20

**Packaged:** 2026-10-30 10:20:11 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_20.zip)

### Summary

General Improvements

### Release notes

Message Designer Routing

- Added a visual routing graph with nodes, connections, and route conditions.
- Added graph search, zoom, folding, saved layouts, and packet-routing traces.
- Preserved hexadecimal routing values through editing, undo, and reopening.

Sandbox Results

- Added structured results for encoding, decoding, round trips, and default checks.
- Improved field inspection, value previews, search, and copying.
- Added paging for large arrays and clearer stale-result, timeout, and decoding-error states.

Field Defaults and Checksums

- New fields default to automatic initialization; advanced fields remain explicitly supplied.
- Checksums can use selected earlier fields or precise byte ranges.
- Checksum selections retain their references through renames and copies.

Binary Message Decoding

- Added object or dictionary output modes.
- Added explicit object-hook, dictionary-hook, and no-hook choices.
- Improved TX, RX, and ANY matching, including Communication Hub direction enums.

Communication Hub

- Added direct integration with generated Message Designer libraries.
- Added live message subscriptions with filtering, bounded queues, and delivery diagnostics.
- Added transmitted-header metadata decoding.
- Improved periodic-send editing and scheduling controls.
- Paused automatic table refresh while inspecting older messages.
- Improved status polling and draining of received messages during shutdown.

Reload and Resource Management

- Unified Soft Restart and source-change reload into one serialized lifecycle.
- Improved rollback when imports or initialization fail.
- Prevented duplicate reloads of the same source revision.
- Improved cleanup of widgets, plots, subscriptions, and replaced resources.
- Blocked stale callbacks from changing the committed runtime.

Config Designer

- Improved its independent window behavior and saved window arrangement.
- Added outline searching, filtering, expansion controls, and icons.
- Preserved outline state through edits and undo.

Documentation and Configuration

- Updated help, API documentation, lifecycle guidance, and benchmark reports.

## Baseline 19

**Packaged:** 2026-10-26 00:48:59 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_19.zip)

### Summary

Message Desginer Field Editor Improvements

### Release notes

Bytes and Strings

- Configurable length prefixes, expressions, and referenced lengths.
- Termination rules and stricter size/encoding validation.
- Hex/UTF-8 editing views and encoded-size feedback.

Conditions and Switches

- Guided conditions and enum selectors.
- Configurable fallback behavior.
- Stable branch identities that preserve values when reordered.

Constants and Calculated Fields

- Typed constant and default values.
- Guided copy, count, sum, and encoded-length operations.
- Better initialization of dependent fields.

Checksums

- Capture actual encoded bytes from fields or ranges.
- Separate custom checksum callable settings.
- Validate checksum output against its storage type.

Field Validation

- Numeric minimum and maximum limits.
- Finite-float constraints.
- VarInt encoded-length limits.
- Padding and alignment checks.
- Configurable handling of unknown enum values.

Editing and Dependencies

- Preserve references across renames, moves, and copies.
- Navigate to referenced definitions and their usages.
- Explain why automatic defaults are unavailable.
- Preserve unfinished editor input.

Default Verification

- Improved constructor and branch initialization checks.
- Detect values altered by decoding hooks.
- Distinguish wire-layout changes from constructor/default changes.

## Baseline 18

**Packaged:** 2026-10-22 23:04:31 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_18.zip)

### Summary

Message Designer improvements

### Release notes

Arrays:

- Added configurable count prefixes, count expressions, byte-length limits, termination rules, and better initialization/default handling.

Enums:

- Added reusable Construct enum schemas with signed/unsigned storage and byte-order settings. Library schema advanced from version 8 to 10.

Editing:

- Added automatic application of valid edits, preservation of unfinished drafts, and improved undo/recovery behavior.

Tree operations:

- Expanded drag-and-drop, reordering, multi-selection, cut/copy/paste, and moving fields, messages, and groups.

Message naming:

- Registry names and behavior mixin names now follow the message name while preserving custom behavior code.

Validation:

- Improved the Hex Sandbox’s default-message checks

## Baseline 17

**Packaged:** 2026-10-22 07:42:38 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_17.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 16

**Packaged:** 2026-10-19 07:29:02 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_16.zip)

### Summary

Framework Assistant

### Release notes

Project understanding:

- Statically indexes Python source without importing or executing it.
- Indexes the offline handbook and saved configuration.
- Finds qualified symbols, owners, annotations, overloads, and source bodies.
- Tracks relationships between buttons, callbacks, helpers, globals, outputs, sessions, and designer selections.
- Detects changed or stale evidence before answering or applying changes.

Retrieval and knowledge browsing:

- Added lexical search across source, configuration, and handbook content.
- Added an offline Knowledge browser.
- Supports English and Turkish handbook aliases.
- Preserves source locations and revision hashes for citations.

Context-window management:

- Tracks estimated and provider-reported token usage.
- Adds configurable context capacity and output reserves.
- Compacts older conversation/tool history while preserving recent exchanges.
- Retries truncated summaries and safely handles cancellation or compaction failure.
- Saves compaction checkpoints with conversation history.

Improved chat experience:

- Redesigned conversation rendering and Markdown formatting.
- Batches streamed text to keep the GUI responsive.
- Preserves scrolling and text selection during streaming.
- Separates reasoning, progress, tool activity, and final answers.
- Adds elapsed-time indicators and collapsible activity details.

Tool activity:

- Added a resizable tool-details sidebar.
- Retains bounded, redacted input/output previews for each tool call.
- Displays failures, truncation limits, source previews, and proposal diffs.
- Keeps repeated tool-call IDs and earlier inspections separate.

Change review:

- Added a structured side-by-side diff viewer.
- Distinguishes added, deleted, empty, and missing-newline files.
- Supports file filtering, navigation between changes, exact row copying, and validation status.
- Ensures approval applies the exact reviewed proposal fingerprint.

Settings:

- Added simple presets and advanced context controls.
- Uses provider/model metadata only when it matches the selected connection.
- Added searchable guidance for every setting.
- Preserves advanced settings when switching modes.
- Added configurable response-header mappings for usage/rate-limit information.

Conversation management:

- Added conversation sidebar navigation and persistence.
- Preserves drafts, manual sidebar sizing, context checkpoints, and reviewed previews across reopening.

Appearance:

- Added a shared Assistant theme, custom controls, icons, rounded surfaces, responsive layouts, and narrow-window behavior.

## Baseline 15

**Packaged:** 2026-10-18 11:27:04 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_15.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 14

**Packaged:** 2026-10-17 09:21:32 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_14.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 13

**Packaged:** 2026-10-16 08:19:43 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_13.zip)

### Summary

Complete native Framework Assistant.

### Release notes

New Assistant window:

- Available in baseline and development modes.
- Opens from the main menu, Config Designer, Message Designer, and callback context menus.
- Keeps conversations, drafts, and inspected data when reopened.
- Not exposed in frozen applications.

Model-server support:

- Connects to OpenAI-compatible /chat/completions servers.
- Supports streaming responses and structured tool calls.
- Provides model listing and connection testing.
- Supports session keys, environment variables, and Windows Credential Manager.

Source-aware assistance:

- Inspects framework source, schemas, generated signatures, examples, and current designer/runtime state.
- Includes a local capabilities browser that works without a model connection.

Local data inspection:

- Supports CSV, JSON, XML, Excel, binary files, MATLAB files, and HDF5.
- Uses bounded previews and subprocess isolation.
- Can locate permitted files under externals/.

Reviewed project changes:

- The model prepares proposals instead of writing immediately.
- Users see exact code/configuration diffs before approval.
- Changes are validated and applied transactionally.
- Supports Save Only, Apply & Reload, and Restore Previous.
- Detects conflicts if files change after review.

Safety and privacy controls:

- Blocks edits to protected framework Python files.
- Protects secrets and sensitive metadata.
- Redacts protected configuration values.
- No shell or arbitrary Python execution tool.
- Assistant history and recovery data are excluded from baseline exports and frozen builds.

Recovery:

- Records transaction journals.
- Recovers interrupted saves during startup.
- Stops startup when external edits conflict with recovery.

Application integration:

- Assistant changes cooperate with source reload.
- Help and Assistant are independent taskbar windows.
- Shutdown safely closes the Assistant.
- Updated starter-page guidance and offline help documentation.

## Baseline 12

**Packaged:** 2026-10-15 00:18:58 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_12.zip)

### Summary

Redesigns Message Designer routing and simplifies its schema.

### Release notes

Added a compiled routing engine:

- Typed identifiers: integers, enums, booleans, bytes, text, and floats.
- Immutable hash-based lookup tables for faster message identification.
- Recursive group routing without scanning every candidate message.
- Better insufficient-data, unknown-route, and ambiguous-route errors.

Simplified Message Designer:

- Removed numeric message IDs from new designer libraries.
- Removed managed tags.
- Removed implicit library/group header layers.
- Every message now explicitly defines all fields in wire order.
- Creating or duplicating a structure no longer automatically creates a wrapper message.
- Message Direction remains supported.

Redesigned routing configuration:

- Groups define identifiers using raw byte positions or common message fields.
- Messages and child groups provide expected values for parent identifiers.
- Entries may be excluded from automatic decoding by leaving assignments incomplete.
- Shared field locations are resolved from actual message layouts.
- Validation reports duplicate routes, invalid expressions, cycles, incompatible fields, and incomplete assignments.

Added backward compatibility:

- Older manifests are migrated to the new schema.
- Legacy shared/group headers become explicit structure fields in affected messages.
- Existing wire layouts are preserved where possible.
- The old numeric-ID registry remains available for legacy code.

Updated generated packages:

- They use compiled wire routing and name-based message registration.
- Generated registries no longer depend on numeric IDs.

Improved Message Designer behavior:

- Opens as an independent admin-gated singleton window.
- Routing and Definitions navigation were streamlined.
- Structure deletion and legacy linked-message handling were updated.

Lifecycle spinner behavior was corrected.

## Baseline 11

**Packaged:** 2026-10-12 23:28:35 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_11.zip)

### Summary

Improves source reloading and runtime safety

### Release notes

Source reload is now user-controlled:

- Default is off.
- Changed callback/external files show a Yes/No prompt.
- auto-reload on|off controls automatic reload and persists in designer/settings.json.

Reloads are transactional:

- New imports and globals are staged first.
- Failed initialization or reload hooks restore the previous working runtime.
- Stale Python bytecode caches are cleared before importing.

File watching now runs in a background thread:

- Prevents slow directory scans from freezing the UI.
- Handles atomic file replacements, rapid same-second edits, new directories, and deleted files.
- Stops cleanly during shutdown.

Added lifecycle feedback:

- The application is temporarily disabled during reload.
- Success and failure messages explain whether changes were applied.

Improved supervisor reliability:

- Upgrade protocol messages bypass redirected GUI output.
- Supervisor output is drained before exit handling.
- Shutdown cancels pending reload prompts and operations safely.

Added compatibility for newer Python-generated class metadata.

## Baseline 10

**Packaged:** 2026-10-12 23:17:56 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_10.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 9

**Packaged:** 2026-10-12 22:55:41 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_9.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 8

**Packaged:** 2026-10-11 20:52:04 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_8.zip)

### Summary

Message Designer and Cmmunication Hub Upgrades

### Release notes

- Communication Hub parser class integration
- Message Designer hierarchical message routing and automatic decoding
- Message Designer routing studio
- Message Desginer type-aware guided defaults

## Baseline 7

**Packaged:** 2026-09-02 07:05:51 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_7.zip)

### Summary

Message Designer and Bug Fix

### Release notes

- Add binary message designer and runtime
- Message Table / Query single session message table pooling when autorefresh enabled fixed

## Baseline 6

**Packaged:** 2026-08-26 01:13:07 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_6.zip)

### Summary

User Experience Improvements

### Release notes

Reworked shutdown handling:

- Allows up to 40 seconds for graceful lifecycle cleanup.
- App now monitors the supervisor process and closes safely if it disappears.
- Replaced the Windows kill-on-close job mechanism with a parent-process watcher.
- Added forced-exit safeguards for stalled shutdowns.
- Hides the main window while the closing loader is displayed.

Improved VS Code integration:

- Resolves Code.exe to the adjacent bin\code.cmd before validation.
- Prevents validation from accidentally opening the VS Code desktop window.
- Runs capability checks asynchronously to avoid freezing the GUI.
- Revalidates VS Code before opening projects, callbacks, or status.
- Added clearer diagnostic commands and error messages.
- Updated the executable picker to accept both Code.exe and code.cmd.

Updated Protocol Insights filters:

- Protocol Insights now select filters saved under Message Table / Query.
- Added saved_query_id and raised the insight schema from version 9 to 10.
- Legacy embedded filters are automatically migrated into saved queries.
- Editing or deleting a saved query synchronizes affected insights.
- Removed the separate Protocol Insight filter editor.

Updated lifecycle callback guidance:

- Closing callbacks now receive the main window rather than a close event.
- Documentation recommends asynchronous callbacks for longer cleanup.

Expanded help content for the new shutdown and VS Code behavior.

## Baseline 5

**Packaged:** 2026-08-24 01:10:51 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_5.zip)

### Summary

User Experience Improvements

### Release notes

- VSCode integration capability gating improvements, each VSCode related operation gated through their requirements
- Apps created directly from baseline N now show that baseline’s release notes under Version → Baseline Release Notes
- A new lifecycle-loader topic covering startup, exit, hard restart, soft restart, upgrade, frozen builds, and failure behavior implemented

## Baseline 4

**Packaged:** 2026-08-23 08:56:51 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_4.zip)

### Summary

VS Code Integration

### Release notes

- VS Code integrated
- IDE Removed
- Created seperate worker and IPC for Variable Explorer
- Help extended

## Baseline 3

**Packaged:** 2026-08-23 03:28:46 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_3.zip)

### Summary

VS Code Integration

### Release notes

- VS Code integrated
- IDE Removed
- Created seperate worker and IPC for Variable Explorer

## Baseline 2

**Packaged:** 2026-08-21 07:14:16 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_2.zip)

**Test baseline**

No summary or release notes were supplied.

## Baseline 1

**Packaged:** 2026-08-20 01:42:31 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_1.zip)

### Summary

First baseline

### Release notes

No detailed release notes were supplied.
