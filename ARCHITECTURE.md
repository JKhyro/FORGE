# FORGE Architecture

## Current stance

FORGE is a Native C-first workspace product.

The preferred implementation stack is:
- Native C for core runtime, child programs, workspace logic, and packaging ownership
- Avalonia only where a managed desktop host or shell is necessary
- Native C interop as the boundary between managed shell surfaces and native workspace components
- C# only where necessary

## Language ownership

Native C owns:
- source and file browsing engines
- editing engines and document-state logic
- review overlays and review-state computation
- note overlays and task-hook behavior
- capability and host-manifest contracts
- packaging policy and native distribution layout

Avalonia and C# may own:
- host window chrome
- shell composition around native child programs
- thin launcher/bootstrap code
- narrowly scoped desktop integration where .NET materially reduces friction

C# should not become the quiet owner of core workspace behavior.

## Interop rules

- Managed and native boundaries must be explicit.
- Interop layers should stay thin and focused on transport, marshaling, lifecycle wiring, and UI-host integration.
- Core logic should not be duplicated on both sides of the boundary.
- If a feature requires C# beyond a thin host concern, that exception should be recorded deliberately before it becomes the default.

## Runtime shape

The intended runtime shape is:
- Native C child programs or libraries for the core workspace surfaces
- an optional Avalonia host shell above those native surfaces
- explicit native capability manifests so FORGE can expose only the surfaces valid for the current host

This keeps the UI shell replaceable while preserving Native C ownership of the product's real behavior.

## Packaging posture

Packaging should treat native binaries as the primary artifacts.

If an Avalonia host is required, it should be packaged as a thin managed shell around the native workspace components rather than the canonical runtime owner.

## First execution implication

The first meaningful execution slice should prove:
- a Native C workspace surface
- a narrow managed host boundary only if needed
- explicit interop ownership
- no drift of core workspace logic into C#
