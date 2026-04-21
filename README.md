# FORGE

FORGE is the code and file workspace product in the SYMBIOSIS suite.

It is integrated into VECTOR and launchable from ANVIL.

## Product boundary

FORGE owns the workspace used to inspect, edit, review, annotate, and task code and files.

Primary scope:
- source and file browsing
- editing surfaces
- review overlays and review-state visibility
- note overlays attached to code and file context
- task hooks that connect workspace activity to upstream workflow systems
- integration contracts with VECTOR, ANVIL, and SYMBIOSIS runtime paths

FORGE does not own broader workflow or project authority.

Boundary rules:
- VECTOR owns the active agent workspace shell and broader interaction surface
- ANVIL owns workflow, project, and execution authority
- SYMBIOSIS owns upstream runtime contracts for routed agent execution
- FORGE stays focused on the code/file workspace rather than absorbing project management, communications, or forge governance

## Runtime base: Hermes-derived FURYOKU

The live agent runtime that reaches FORGE's workspace through the SYMBIOSIS routing contract has moved from OpenClaw to Hermes Agent. Hermes-derived FURYOKU is the runtime spine for the 7-Symbiote swarm; OpenClaw is demoted to a feature-harvest lane, not a host runtime. FORGE's code/file workspace boundary is unchanged by the move. Anchor is universalized across `JKhyro` Project #20 (FURYOKU) and Project #10 (SYMBIOSIS).

- Authoritative migration plan: [`FURYOKU/docs/hermes-furyoku-migration.md`](https://github.com/JKhyro/FURYOKU/blob/main/docs/hermes-furyoku-migration.md)
- OpenClaw carryover rules: [`FURYOKU/docs/openclaw-carryover-inventory.md`](https://github.com/JKhyro/FURYOKU/blob/main/docs/openclaw-carryover-inventory.md)

## Implementation direction

FORGE is now Native C first.

Implementation rules:
- Native C is the default language for core workspace logic, child programs, review/note/task behavior, interop ownership, and packaging logic.
- Avalonia may be used for desktop host or shell surfaces when a managed UI layer is necessary, but it should sit over Native C components rather than replacing them.
- Native C interop must stay explicit and narrow, with stable ABI boundaries between Native C components and any managed host layer.
- C# is allowed only where necessary for Avalonia, thin bootstrap layers, or platform integration that is materially simpler in .NET.
- Core workspace behavior should not drift into C# unless a narrow exception is documented first.

## First execution wave

The first meaningful delivery wave for FORGE is:
- native C source browsing baseline
- native C editing baseline
- native C note-overlay baseline
- task-hook contract into upstream systems
- explicit Avalonia host boundary only where needed
- integration contract clarity with VECTOR and ANVIL

This wave should produce one narrow vertical slice that proves the workspace boundary without widening into full project-management or forge-platform ownership.

See [ARCHITECTURE.md](/C:/KHYRON/apps/FORGE/ARCHITECTURE.md) for the current Native C and interop posture.
