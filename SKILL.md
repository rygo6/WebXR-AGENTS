---
name: webxr
description: Answer questions and help implement or debug browser-based XR by referencing local WebXR specification and official sample repositories. Use for the WebXR Device API, navigator.xr, XRSession, XRFrame, poses and views, reference spaces, input sources and gamepads, WebGL or WebGPU bindings, immersive-vr, immersive-ar, hit testing, anchors, hand input, layers, permissions, privacy, browser behavior, and WebXR sample code. Always consult the local repos before answering.
---

# WebXR Local Reference Skill

Always consult the relevant repositories in this skill's `references/` folder:

```text
references/WebXR/                 ← Core WebXR Device API specification and explainers
references/WebXR-AR-Module/       ← Immersive AR sessions and environment blending
references/WebXR-Hit-Test/        ← Real-world hit testing
references/WebXR-Anchors/         ← Tracked anchors
references/WebXR-Layers/          ← WebXR compositor layers
references/WebXR-Hand-Input/      ← Articulated hand input
references/WebXR-Gamepads/        ← XR gamepad mapping
references/WebXR-Input-Profiles/  ← Controller profiles, assets, and helper libraries
references/WebXR-Samples/         ← Official runnable examples and shared sample code
```

WebXR is the browser-facing API. Use the separate `openxr` skill for the native Khronos runtime API.

## Choose the authoritative repository

Route the question before searching:

| Topic | Primary repository |
|---|---|
| Sessions, frames, views, poses, reference spaces, core input, permissions | `references/WebXR/` |
| `immersive-ar`, environment blend mode, interaction mode | `references/WebXR-AR-Module/` |
| `XRHitTestSource`, transient hit testing, hit test results | `references/WebXR-Hit-Test/` |
| `XRAnchor`, anchor creation, tracking, persistence | `references/WebXR-Anchors/` |
| `XRWebGLBinding`, projection/quad/cylinder/equirect/cube layers | `references/WebXR-Layers/` |
| `XRHand`, joints, joint poses, hand-tracking feature | `references/WebXR-Hand-Input/` |
| `XRInputSource.gamepad` and XR gamepad mapping | `references/WebXR-Gamepads/` |
| Hardware profile registry, controller models, motion-controller helpers | `references/WebXR-Input-Profiles/` |
| Runnable usage patterns | `references/WebXR-Samples/` |

For module features, read both the module repository and any core definitions it extends. For questions spanning multiple features, consult every matching row plus core; for example, AR placement with hit testing and anchors requires the AR, Hit Test, Anchors, and core repositories. Prefer `index.bs` for normative behavior; use explainers for rationale and examples.

## Answer API and behavior questions

1. Select the authoritative repository from the table above.
2. For specification repositories, search `index.bs` for the interface, IDL member, definition, or algorithm. Also search `references/WebXR/index.bs` when the module extends core types. Input Profiles and Samples are code/data repositories instead: inspect their READMEs, registries or package sources, relevant HTML, and imports.
3. Read the surrounding normative steps and linked definitions, not only the matching line.
4. Use explainers for conceptual and non-normative context. In the core repository:
   - `explainer.md` for the overall API and session lifecycle
   - `input-explainer.md` for input sources, targeting, and select events
   - `spatial-tracking-explainer.md` for poses and reference spaces
   - `privacy-security-explainer.md` for permissions and data exposure
   - `accessibility-considerations-explainer.md` for accessibility guidance
   - `webvr-migration.md` for legacy WebVR migration
5. State when a feature belongs to a separate Immersive Web module rather than the core Device API.

## Answer implementation questions

1. Start with the closest example in `references/WebXR-Samples/`.
2. Follow its imports into `references/WebXR-Samples/js/` to distinguish shared helpers from browser API calls.
3. Cross-check each relevant API call against its module's `index.bs` and the core `references/WebXR/index.bs`.
4. Treat samples as illustrative code, not normative requirements or proof of browser support.

## Find the right sample

| Topic | Start here |
|---|---|
| Session setup | `immersive-vr-session.html`, `immersive-ar-session.html`, `inline-session.html` |
| Input | `input-tracking.html`, `input-selection.html`, `controller-state.html`, `immersive-hands.html` |
| Spaces and movement | `room-scale.html`, `teleportation.html` |
| AR placement | `hit-test.html`, `hit-test-anchors.html`, `anchors.html` |
| Layers | `layers-samples/` |
| WebGPU | `webgpu/` |

Also inspect `proposals/`, `shaders/`, and `tests/` when the question concerns experimental features, rendering details, or expected sample behavior.

## Answering strategy

- Always search or read local files before answering.
- Separate normative specification requirements, sample conventions, and browser-specific behavior.
- Do not infer current browser support from the presence of a sample; verify current compatibility when it matters.
- Cite the repository-relative files used so the user can follow the evidence.
- If a reference submodule is absent, report that limitation and initialize it before relying on memory or another repository.
