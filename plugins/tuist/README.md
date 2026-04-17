# Tuist Plugin

This plugin packages the hosted Tuist MCP server in `plugins/tuist`.

## What It Covers

- inspecting live Tuist project data through MCP, including projects, Xcode builds, Gradle builds, test runs, cache runs, generations, bundles, and artifact trees
- using Tuist MCP prompts for build comparisons, flaky test investigation, cache and generation regressions, bundle diffs, and selective testing analysis

## Plugin Structure

The plugin lives at:

- `plugins/tuist/`

with this shape:

- `.codex-plugin/plugin.json`
  - required plugin manifest
  - defines plugin metadata and points Codex at the plugin contents

- `.mcp.json`
  - plugin-local MCP config
  - connects Codex to the hosted Tuist MCP endpoint

- `assets/`
  - plugin icons referenced by the manifest

- `agents/`
  - plugin-level agent metadata

## Notes

This plugin is MCP-backed, not app-backed. Authentication for the MCP server happens through OAuth, and the endpoint uses Tuist's read-only `mcp` scope group.

This bundle is intentionally MCP-only. The MCP server and its prompts are implemented in the Tuist platform itself, so the plugin does not duplicate that logic as local Codex skills.
