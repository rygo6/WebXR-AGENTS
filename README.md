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

Install once into the shared agent skills directory, then symlink it into each agent's skills folder.

The reference repos are git submodules. Initialize them one level deep only — they are read-only
references that are never built, so nested build dependencies are pure overhead:

```bash
git clone git@github.com:rygo6/WebXR-AGENTS.git ~/.agents/skills/webxr
cd ~/.agents/skills/webxr
git submodule update --init
git submodule update --remote
```

Do not pass `--recursive` or clone with `--recurse-submodules`.

Then link it into the agents you use:

```bash
mkdir -p ~/.claude/skills ~/.codex/skills
ln -s ~/.agents/skills/webxr ~/.claude/skills/webxr
ln -s ~/.agents/skills/webxr ~/.codex/skills/webxr
```

On Windows, use `mklink /J` to create a junction instead (run in `cmd`, no admin rights needed):

```bat
mklink /J "%USERPROFILE%\.claude\skills\webxr" "%USERPROFILE%\.agents\skills\webxr"
mklink /J "%USERPROFILE%\.codex\skills\webxr"  "%USERPROFILE%\.agents\skills\webxr"
```

## Usage

Once installed, invoke `/webxr` from any agent that supports skills.
