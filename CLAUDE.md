# Vigil

Lightweight native macOS app to supervise Claude Code sessions.
Built with Tauri v2 (Rust shell, zero custom Rust code) + React + TypeScript.

## What it is
A 3-panel supervisor UI — not an IDE.
- Left: live file tree of the current working directory
- Right: read-only code viewer with syntax highlighting (click a file to open)
- Bottom: embedded shell terminal (supports any shell + claude CLI)
- Top bar: git diff badge — files modified since last commit, click to see diff

## What it is NOT
No file editing. No extensions. No debugger. No linter. Observer only.

## Stack
- Tauri v2 with official plugins only:
  - tauri-plugin-fs (file tree + watcher)
  - tauri-plugin-shell (terminal)
- React + TypeScript frontend
- xterm.js for the terminal panel
- shiki for syntax highlighting (read-only viewer)
- simple-git (Node side) via Tauri sidecar for git diffs

## Layout
[ File Tree 250px ] [ Code Viewer / Diff Viewer flex-1 ]
[        Terminal (bottom, resizable, ~40%)              ]

## Principles
- No Electron, no heavy runtime — WKWebView native macOS
- Bundle size target < 10MB
- Single window, no tabs, no workspaces
