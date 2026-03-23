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

## First execution wave

The first meaningful delivery wave for FORGE is:
- source browsing baseline
- editing baseline
- note-overlay baseline
- task-hook contract into upstream systems
- integration contract clarity with VECTOR and ANVIL

This wave should produce one narrow vertical slice that proves the workspace boundary without widening into full project-management or forge-platform ownership.
