# Baseline Notes

Release summaries and notes from `baseline-package.json` inside each ZIP, listed in descending baseline order (newest first).
Baselines with neither a summary nor release notes are marked **Test baseline**. Recorded wording is retained; list formatting is normalized for Markdown.
Package timestamps use Europe/Istanbul time (UTC+03:00).

## Baseline 27

**Packaged:** 2026-11-05 07:50:39 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_27.zip)

### Summary

Common raw RX/TX message retention across Communication Hub transports

### Release notes

#### Raw Message Retention

- Extended optional raw RX/TX message retention to TCP client, TCP server, Serial, Telnet, and Raw Ethernet sessions.
- Kept original message bytes in raw_frame alongside parsed output, including reconstructed receive messages and supplied transmit bytes.
- Preserved raw bytes through process handoff and storage snapshots while retaining the existing Raw Frame Hex export support.

#### Storage Settings and Migration

- Moved Retain complete raw RX/TX messages after parsing into the common Storage tab under storage.retain_raw_frames.
- Kept retention enabled by default for Raw Ethernet and disabled by default for the other transports.
- Added automatic migration from the earlier Ethernet transport setting. An explicit storage setting takes precedence, and invalid non-boolean values fail validation.
- New-session defaults follow the selected protocol until the user makes an explicit retention choice.

#### Documentation and Verification

- Updated built-in help and transport documentation with common retention behavior, settings migration, and memory implications.
- Added tests for defaults, migration, validation, RX/TX parsing, process handoff, storage restoration, form round trips, and framed TCP receive/send retention.
- The focused retention, Raw Ethernet, and baseline test run completed with 47 passing tests and one skipped test out of 48.
- Package payload hashes, Python syntax, bundled source, and the recovery archive were verified.

## Baseline 26

**Packaged:** 2026-11-05 01:00:11 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_26.zip)

### Summary

Communication Hub raw Ethernet capture, sending, and frame inspection

### Release notes

#### Raw Ethernet Sessions

- Added a Windows/Npcap Raw Ethernet transport to Communication Hub's existing I/O, parser, and storage pipeline.
- Added background adapter discovery, saved adapter selection, manual adapter identifiers, and capture configuration controls.
- Added EtherType, source MAC, destination MAC, and advanced BPF filters, including EtherType matching through single and double VLAN tags.
- Added capture direction, promiscuous mode, snapshot length, driver buffer, timeout, frame-size, and raw-retention settings.

#### Packet Capture and Sending

- Preserved each captured packet as one complete parser message, including Ethernet headers, VLAN tags, and padding.
- Added Ethernet header and capture metadata, including source/destination addresses, type or length, VLAN fields, capture origin, truncation, and decode errors.
- Added manual and periodic full-frame sending with byte and size validation. Successful TX records represent native adapter submission.
- Added bounded background native reads, cancellation-aware send handling, restart cleanup, and separate capture, submission, and driver-drop metrics.

#### Storage, Export, and Interface

- Retained raw frames through parsing, process handoff, table persistence, and Excel export, with a Raw Frame Hex export column.
- Added Ethernet session summaries, sending guidance, capture diagnostics, and parser controls aligned with packet-based framing.
- Expanded built-in help and documentation with Npcap setup, capture settings, receive/send contracts, filtering, and troubleshooting.

#### Verification and Requirements

- Added fake-backend and native API tests for packet decoding, filtering, adapter discovery, capture, sending, cancellation, shutdown, persistence, export, and the three-process pipeline.
- Raw Ethernet sessions require the separately installed Windows Npcap runtime. Hardware acceptance with real adapters and independent packet capture remains outstanding.
- All seven baseline tests and the exported application smoke test passed.
- The Communication Hub suite ran 191 tests with 189 passing and two skipped. The focused Raw Ethernet suite ran 32 tests with 31 passing and one skipped.

## Baseline 25

**Packaged:** 2026-11-04 07:17:52 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_25.zip)

### Summary

Unified Assistant workflow, runtime actions, and optional stage model selection

### Release notes

#### Unified Assistant Workflow

- Made inspection, authoring, validation, and review the common Assistant execution path and removed the legacy single-agent service and workflow selector.
- Required current review clearance before applying drafts, including drafts retained from older versions.
- Added a dedicated runtime-action stage with restricted tools and an explicit Run Action confirmation. Mixed edit/action tasks defer action preparation until the edits are applied.
- Improved action ownership, stale-action checks, interrupted-action recovery, and restoration of the previous Assistant transaction.

#### Optional Model Selection by Stage

- Added an Agent Models settings tab with optional model choices for Inspect, Author, Review, and Action on the configured server.
- Added deterministic automatic assignment using advertised capabilities, context capacity, saved preferences, and assignment load. Multi-model selection defaults to off.
- Applied the selected stage model's context, output, streaming, token parameter, and reasoning settings while sharing the workflow deadline, request limits, and cancellation.
- Added stage model attribution, provider-reported model identity, and recorded reasons for preference fallback.

#### Evidence and Requirement Checks

- Improved evidence selection for cited source locations and retained distinct inspected ranges during answer review.
- Added static checks for explicitly requested scalar callback return values.
- Improved Python example syntax diagnostics and recovery guidance for missing layout targets.
- Extracted bounded initial prompt construction for the shared workflow.

#### Evaluation and Maintenance

- Extended task, dialogue, and reliability evaluators with routing controls, per-model reporting, and workflow repair scenarios.
- Added offline model-routing and workflow-oracle tests and updated workflow and model-selection documentation.
- Removed tracked Assistant and test bytecode caches.
- All seven baseline tests and the exported application smoke test passed.
- The Assistant suite ran 467 tests. 462 passed, one was skipped, and three failed with one error. Failures covered the working animation lifecycle, narrow composer controls, and streaming GUI heartbeat. Tool-activity correlation raised a missing path error. These issues remain unresolved in this snapshot.

## Baseline 24

**Packaged:** 2026-11-03 12:30:08 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_24.zip)

### Summary

Assistant answer handling, handbook retrieval, and smoother chat scrolling

### Release notes

#### Assistant Answers and Task Completion

- Separated the user-facing answer from the task label and change review summary. Explanation turns now require an actual reply, and streamed tool responses display the answer field.
- Added bounded retries for empty replies and clearer incomplete-response messages. Blank replies are excluded from the correction exchange.
- Updated Assistant instructions to respond in the user's language, answer greetings directly, and provide concrete steps with relevant installed handbook references.

#### Handbook Retrieval

- Raised the search rank of handbook sections whose full title appears in the question.
- Guided the sequential workflow to use an existing handbook excerpt when it covers the requested procedure and inspect additional material for specific gaps.

#### Chat Streaming and Navigation

- Preserved the visible reading position during chat updates and added Jump to latest to resume following new replies.
- Kept incomplete Markdown code fences formatted during streaming and progressively revealed buffered answers when streaming is enabled.
- Adjusted prompt bubble width to fit the message and available chat space.

#### Verification

- Added regression coverage for streamed answers, buffered replies and scroll following, empty-response recovery, and rejection of summary-only explanations.
- All seven baseline tests and the exported application smoke test passed.
- The Assistant suite ran 441 tests. 438 passed, one was skipped, and two previously documented UI tests still failed, covering the working animation lifecycle and narrow composer controls.

## Baseline 23

**Packaged:** 2026-11-03 11:30:43 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_23.zip)

### Summary

Compact framework dialogs with expandable, copyable details

### Release notes

#### Shared Message Dialogs

- Added a shared dialog for errors, warnings, confirmations, and status messages.
- Show a short, wrapped summary by default. Show Details opens a bounded, scrollable view of the full plain-text message.
- Copy places the complete message on the clipboard without closing the dialog. Long paths and unbroken text wrap within the available width.
- Preserve standard button results and default choices. Closing a Yes/No confirmation selects No.

#### Framework and Project Operations

- Applied the shared dialog to baseline and app release notes, baseline export and upgrade feedback, build errors, project recovery, and VS Code diagnostics.
- Made runtime tracebacks available through Show Details and Copy Traceback.
- Added Copy to the source-change reload prompt, including the pending file paths.

#### Designer and Tool Workflows

- Adopted the dialog for validation and confirmations in Configuration Designer, Message Designer, Routing Studio, Communication Hub, and Protocol Insights.
- Added concise prompts for potentially breaking Message Designer saves, generated-file overwrites, and structure deletion choices.
- Applied copyable messages to selected Assistant review, output transfer, Variable Explorer, FTP, macro, and help workflows.

#### Verification

- Added tests for long-message wrapping, expandable details, full-message copying, and safe dismissal. Updated affected tests to intercept the shared dialog.
- All 17 focused dialog, baseline, and Assistant review tests passed. The broader affected suite reported failures.

## Baseline 22

**Packaged:** 2026-11-03 01:20:41 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_22.zip)

### Summary

Assistant task continuity, sequential workflow preview, and clean baseline exports

### Release notes

#### Assistant Task Continuity and Clarification

- Added structured tasks with persistent requirements, constraints, decisions, questions, and draft references.
- Added semantic task start, resume, amendment, cancellation, and topic switching while retaining earlier drafts and accepted decisions.
- Added choice buttons, free-text answers, optional delegated choices, and mode-switch cards. Required answers pause dependent work; clarification does not grant editing or runtime-action permission.
- Preserved task context across compaction, history reload, and workflow checkpoints, with transcript and revision checks for stale state.

#### Sequential Workflow Preview

- Added an opt-in workflow using the selected model sequentially for inspection, authoring, and review, with separate stage contexts and shared task budgets.
- Added requirement coverage, candidate-file review, bounded repair cycles, transactional checkpoints, and recovery of interrupted runs.
- Tied review clearance to the candidate, task, and project revisions. Apply remains an explicit user operation, and incomplete review blocks Apply.
- Kept runtime-action preparation in Single agent mode; the sequential preview does not automatically apply changes, execute generated code, or switch models.

#### Source-backed Answers and Recovery

- Added static validation of Python API examples against installed source, including imports, facade methods, arguments, settings fields, and bindings across code blocks.
- Kept standalone Serial and Communication Hub API evidence distinct through follow-up questions.
- Added source/help evidence sharing, citation identity and revision checks, bounded answer correction, and recovery guidance when evidence is insufficient.
- Improved context compaction and tool-call pairing so current corrections, inspected evidence, and task decisions survive longer conversations.

#### Authoring and Model Compatibility

- Added focused capability contracts and typed authoring support for layouts, tabs, buttons, callbacks, helpers, outputs, message libraries, and session actions.
- Added atomic page/button/output proposals, independent outcome checks, and clearer repair guidance while preserving existing project content.
- Added server-advertised reasoning options and context-limit discovery, bounded requests, streaming deadline checks, and structured response streaming.

#### Chat Experience

- Added prompt copying, conversation rename/delete controls, formatted streamed responses, and updated conversation styling.
- Improved per-turn progress/status presentation, elapsed activity, cancellation controls, and settings/help content for workflow and reasoning options.

#### Baseline Packaging and Supervisor

- Added baseline_configs with clean starter project settings, callbacks, and helper packages, independent of live development files.
- Export now excludes development history, Assistant state, tool output, and Python caches; framework help, branding, and product identity use current source.
- Missing or invalid starter files stop export. Release metadata, payload hashes, installed manifests, and source recovery archives are generated from the staged payload.
- Excluded development tests and local sibling modules from supervisor dependency discovery, and rebuilt designer.exe from the current supervisor source.

#### Documentation and Verification

- Added workflow, semantic-task, API-validation, evidence-recovery, capability evaluation, and reliability documentation and regression fixtures.
- Current verification: 435 Assistant tests passed, one skipped, and two failed out of 438; all seven baseline tests and eight supervisor tests passed. The exported-application smoke test passed with 219 indexed files and 124 help topics.
- Known UI test failures, reproduced individually: test_working_animation_follows_task_and_window_lifecycle and test_composer_controls_remain_adjacent_without_overlap_at_narrow_width. This baseline preserves the requested current state with these failures unresolved.
- Sequential execution remains an opt-in preview. Broader repeated model qualification and multi-turn reliability gates remain open; deterministic checks and development evaluations do not establish general model reliability.

- Framework source: https://github.com/SakirVarli/framework/commit/40e18828563c63afb59f96f2aa2528ff721b0373

## Baseline 21

**Packaged:** 2026-11-01 23:22:16 (UTC+03:00)

**Version:** 0.1.0 | **Build:** 1

[Download ZIP](https://github.com/SakirVarli/framework-baselines/raw/refs/heads/main/baselines/SAKiR_GUI_baseline_21.zip)

### Summary

Communication Hub pipeline and Message Designer protocol improvements

### Release notes

Communication Hub Pipeline

- Replaced the previous session backends with separate I/O/framing, stateful parser, and storage/subscription processes, with automatic migration of supported saved configurations.
- Added an IPC configuration tab with record and byte budgets, batching controls, and block/drop overload policies.
- Shared equivalent source-filter evaluation between API subscriptions and Protocol Insights while keeping their callback and processing state independent.
- Added capture-to-storage barriers, bounded query caching, retained-table reads after capture stops, and ordered replay/live handover.
- Improved shutdown draining and diagnostics for queued records, in-flight bytes, drops, blocked handoffs, parser failures, and incomplete shutdowns.

Message Designer Length Fields

- Added encoded-byte length fields for whole messages or structures, selected fields, field ranges, and byte ranges.
- Automatic lengths are calculated for construction and encoding; manually initialized lengths are checked against the actual encoded payload.
- Verified received lengths during decoding and resolved final length bytes before checksum calculation.
- Updated the message-library schema from version 11 to 12 while retaining migration support for existing libraries.

Checksums and Enum Storage

- Expanded checksum algorithms with SUM16, SUM32, XOR8, CRC8, CRC16/MODBUS, CRC16/CCITT-FALSE, and Adler32, with storage-capacity checks.
- Added enum storage using packed bit integers, arbitrary-length byte integers, VarInt, and ZigZag.
- Preserved enum aliases, unknown-value policies, guided defaults, numeric JSON exports, and applicable routing/size analysis.

Routing and Definition Editing

- Added Get expected values from defaults and Push expected values to defaults, with reviewed previews and atomic undoable transfers.
- Improved routing-graph layout, connector positioning, click/drag behavior, and undo for visual layout changes.
- Added batch deletion through the Delete key and context menus, with dependency checks, a single undo step, and predictable selection afterward.

Startup and Restart

- Passed Windows foreground permission through the application and supervisor during restart so the replacement application can activate.
- Kept lifecycle feedback windows from taking focus and rebuilt the supervisor executable.

Documentation and Verification

- Added guides for the current Communication Hub pipeline, IPC settings, length fields, checksum algorithms, enum storage, and routing-default workflows.
- Added regression tests and end-to-end, multi-session, IPC, and architecture benchmark reports.

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
