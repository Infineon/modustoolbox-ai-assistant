# Change Log

All notable user facing changes to this project will be documented in this file. The format is based on [Keep a Changelog](http://keepachangelog.com/)

## 0.8.0 - 2026-10-23

### Skills and Device Guidance

- Extended the `mtb-debug-workflow` skill to TRAVEO™ T2G, PSOC™ 6, and PSOC™ 4 boards, so the AI assistant can now diagnose crashes on CM7, CM4, and CM0+ cores as well as on PSOC™ Edge E84. Crash reports now name the fault type and the source line where it happened, and warn when the firmware on the board is older than your source code.
- Replaced incompatible C3-specific guidance for PSC3M7/M8/P7/P8 with a limitation notice, while retaining common skills and instructions.
- Added TRAVEO™ T2G- and PSOC™ 4-specific agent instructions and workspace overviews.
- Added Device Configurator guidance for PSOC™ 4 HV.

### Discovery and Project Planning

- Added device-neutral agent instructions and MCU-based skill fallback for custom BSPs and added related-board catalog fallback for custom BSPs, with explicit substitution notices while allowing manifest entries to declare both board and MCU matches, with board-first fallback.
- Added ranked code-example search using board vocabulary and free-text queries.

### Fixes and Reliability

- Restore retries after failed initial manifest loads, including caller-recovered panics, while keeping selected sources fixed until server restart.
- Board-not-found errors in generated workspace documentation now include the loaded manifest URLs or local paths to help diagnose source selection.
- Added **Configure Documentation Auto Refresh** to the Command Palette to open the workspace documentation refresh setting directly.
- Select manifest sources at startup using Local Content Mode, environment or China/custom URL overrides, local manifest lists, and installed content packs. Tech packs load without an EAP; only the selected EAP supplements the base catalog. Local files bypass disk caching; remote refreshes no longer block catalog requests.
- Implemented **Restart ModusToolbox MCP Server** without reloading the VS Code window. Effective manifest-source setting changes offer **Restart & Regenerate Instructions**, **Restart MCP Server**, or **Later**. The combined action explicitly regenerates after a successful restart; restart-only respects auto-refresh settings. Use the command manually after pack upgrades or local manifest edits.
- Improved workspace-analysis error reporting and prevented cascading instruction-generation failures.
- Fixed stale pre-rename skill sessions and improved periodic manifest refresh.
- Fixed BSP detection to use the project's configured target.

## 0.6.0 - 2026-09-28

### Public Support and Issue Tracking

- Added links to the [public support repository](https://github.com/Infineon/modustoolbox-ai-assistant) and [issue tracker](https://github.com/Infineon/modustoolbox-ai-assistant/issues) for bug reports, feature requests, and usage questions.

### Skill Updates

- Added prompts to regenerate deployed skills and instructions when the extension version changes, with an option to suppress reminders for that version.
- Added user-visible error reporting for exceptions while loading or copying manifest-selected AI assets.
- Updated the supported-device list to include PSOC™ 4 HV and TRAVEO™ T2G as supported in preview.
- Added an SCB LIN slave middleware skill for the PSOC™ 4000T family.
- Added an HPPASS analog subsystem skill for PSOC™ Control C3 (PSC3M5/PSC3M6) covering SAR ADC, CSG comparator/DAC, Autonomous Controller state tables, and 3P3Z filter bring-up. It is now deployed to all Control C3 boards.
- Added the `mtb-multi-core-retarget-io` skill for PSOC™ Edge E84 devices to guide multi-core `printf()` setup. Library-installation guidance now checks debug UART ownership to avoid conflicting output from multiple cores.
- Added the `mtb-smif-storage` skill for TRAVEO™ T2G CYT3DL, CYT4DN, CYT4BF, and CYT6BJ devices, which sets up SMIF external flash and PSRAM, including XIP memory-mapped access.

### Discovery and Project Planning

- Added keyword and category filtering, category summaries, and keyword-search result limits to code-example discovery, reducing the amount of catalog data needed in AI conversations.
- Improved project planning to verify available skills for the selected board, validate board and template choices, and confirm proposed project names and directories before project creation.

## 0.5.0 - 2026-08-28

- Added device-aware deployment so generated AI instructions and skills match the active board and MCU, with obsolete generated assets removed.
- Expanded preview guidance for PSOC™ Edge E84 and PSOC™ Control C3, including Control C3 configuration, debugging, FreeRTOS, and retarget-I/O workflows.
- Improved project creation handoff, board skill discovery, and ModusToolbox build workflows.
- Improved extension responsiveness and MCP session cleanup during AI asset and tool operations.
- Included the README and changelog in packaged extensions so VS Code can display release documentation.

## 0.1.21 - 2026-05-21

- Changed extension id. Now "modusToolbox-ai"
- Changed logger identifiers to "mtbai.ext" and "mtbai.srv" for the extension and server respectively
