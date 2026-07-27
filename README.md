# WebXR-Agents

An agent skill that answers WebXR questions using locally cloned specifications, input-profile data, and official samples instead of relying only on training data.

### Reference repos included

| Repo | Purpose |
|---|---|
| `references/WebXR` | WebXR Device API specification source (`index.bs`) and explainers |
| `references/WebXR-AR-Module` | WebXR Augmented Reality Module |
| `references/WebXR-Hit-Test` | WebXR Hit Test Module |
| `references/WebXR-Anchors` | WebXR Anchors Module |
| `references/WebXR-Layers` | WebXR Layers API |
| `references/WebXR-Hand-Input` | WebXR Hand Input Module |
| `references/WebXR-Gamepads` | WebXR Gamepads Module |
| `references/WebXR-Input-Profiles` | Input profile registry, controller assets, and helper libraries |
| `references/WebXR-Samples` | Official runnable examples, shared helpers, layers samples, and WebGPU samples |

## Installation

Clone with `--recurse-submodules` because the reference repositories are Git submodules:

```bash
git clone --recurse-submodules git@github.com:rygo6/WebXR-AGENTS.git ~/.agents/skills/webxr
```

Then link it into the agents you use:

```bash
mkdir -p ~/.claude/skills ~/.codex/skills
ln -s ~/.agents/skills/webxr ~/.claude/skills/webxr
ln -s ~/.agents/skills/webxr ~/.codex/skills/webxr
```

## Usage

Once installed, invoke `/webxr` from any agent that supports skills.
