# Tuist Plugin

This plugin packages Tuist workflows in `plugins/tuist`.

It combines:

- the hosted Tuist MCP server at `https://tuist.dev/mcp`
- a small set of local Tuist skills for generated-project workflows

## Included skills

- `using-tuist-generated-projects`
- `migrating-to-tuist-generated-projects`
- `debug-generated-project`

## What It Covers

- working day to day in Tuist-generated Xcode workspaces
- migrating existing Xcode projects to Tuist-generated workspaces
- debugging `tuist generate` failures and generated-project issues
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

- `skills/`
  - local skill payload for generated-project, migration, and debugging workflows

- `assets/`
  - plugin icons referenced by the manifest

- `agents/`
  - plugin-level agent metadata

## Notes

This plugin is MCP-backed, not app-backed. Authentication for the MCP server happens through OAuth, and the endpoint uses Tuist's read-only `mcp` scope group.

The MCP server and its prompts are implemented in the Tuist platform itself. The plugin bundles only a small set of complementary local skills so users can handle both local workspace work and hosted insight workflows from one install.
