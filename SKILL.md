# Papercut Reels

## What this skill is

- Use this skill to run the papercut-explainer repo installed on this machine and to make layered construction paper explainer reels with it.

- Treat the repo's own nine skills as the pipeline authority. This skill records where everything lives on this machine, what is installed, and the local workarounds, and it points each stage at the right repo skill.

- Find the repo skills linked in `~/workspace/custom-skills/` beside this one, with names that start with `papercut-`. Read the matching SKILL.md before running a stage.

## The setup on this machine

- Repo home is `/home/hatch/workspace/papercut-explainer` and the Remotion library is `/home/hatch/workspace/papercut-explainer/library`.

- Resolve the library path from the `PAPERCUT_LIB` line in `~/.config/papercut-explainer/config.env` when a repo skill asks for it. The same file holds `PAPERCUT_PY`, the Python venv the QA tools use.

- Install mode is Standard, installed 2026-11-23. Strategy, hook, script, storyboard, build and QA all work, and full reels render with a placeholder voice.

- Local voiceover is not installed. Full mode adds a Qwen3-TTS venv and a model download of 4 to 6 GB, and the user has not asked for it. Do not promise a generated voice until `./install.sh --mode full` has been run from the repo root.

- Check the setup any time with `./install.sh --doctor` from the repo root. The self-test passed at install time with a scaffold, a typecheck and a still render.

- Set `CHROME_PATH` to `/home/hatch/.cache/ms-playwright/chromium_headless_shell-1248/chrome-headless-shell-linux64/chrome-headless-shell` when a render step says no Chrome or Chromium was found. The audio render needs a Chrome binary and the Playwright headless shell is the one on this machine.

- Point `TMPDIR` at `/home/hatch/workspace/tmp` for installs and first project setups. The system temp folder is small and the first project's node_modules run to about 0.7 GB.

## Run a reel

- Start with the repo's `papercut-explainer` router skill when the user asks for a reel end to end or does not name a stage. It offers run modes from a full reel down to a single stage, so confirm the mode before building anything.

- Ask only for the intake items the router lists and only when they are missing. The source link, the one claim the video proves, the call to action keyword and what the viewer gets for it, the length, and any accent colour or mascot.

- Default to 22 to 30 seconds at 1080 by 1920 when the user gives no length. The style runs about 20 to 45 seconds of vertical video with a taped headline banner per beat and word by word torn paper captions.

- Work through the stages in order and let each stage read the files the stage before it wrote. Strategy writes the brief, hook writes the hook block, script writes the narration and staging table, storyboard writes the camera and cut table, build scaffolds and renders, voice times the narration, and QA checks stills against the storyboard.

- Run one stage on its own when the user names it, such as a hook rewrite or a storyboard for an existing script. Each stage skill works standalone.

- Keep the pipeline in the project files, not in chat. An episode can resume from any stage in a later session because every stage reads and writes files.

## Render and deliver

- Expect renders to be slow on this machine because it has no GPU. Show stills or a short cut early and give an honest time estimate before a full render, the same discipline as the `long_render_progress` skill.

- Deliver the finished MP4 from the episode project's `out/` folder and attach it in the reply. Name what is placeholder in it, above all the voice, when the reel used one.

- Run the QA stage before calling a reel done. Compare stills against the storyboard and the style guide and fix what QA flags, or say plainly what was left unfixed.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.
