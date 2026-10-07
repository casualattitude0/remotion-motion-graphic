# Remotion video workspace

## Project boundary

Each video is an independent Remotion project living in its own subdirectory of this workspace. A project's scope is the directory holding its `package.json` and everything beneath it.

- **Current project**: the video the user names; when none is named, the project that owns the files under discussion. When that is unclear, ask the user first.
- Reading, searching, editing, and running commands all stay inside the current project directory. Root every `grep`, `find`, and glob at the current project directory, never at the workspace root.
- Files in another video project may be read only when the user explicitly points to them (e.g. "reuse the transition from `intro`"), and then only that project and that scope.
- When another project's approach would help but the user has not pointed to it, ask the user instead of looking.

## Adding a video

From the workspace root, scaffold each video into its own subdirectory:

```bash
npx create-video@latest --yes --blank <video-name>
```

`--yes` needs both a template flag and a directory name, otherwise the scaffolder drops into interactive mode and hangs. Other templates: `npx create-video@latest --help`.

The workspace root holds only `CLAUDE.md`, `AGENTS.md` (a symlink to `CLAUDE.md`; edit either, they are one file), `README.md`, `.claude/` (workspace skills and launch config), and the project directories.

## Commands

Run each project's commands from inside that project directory, following its own `package.json` scripts.
