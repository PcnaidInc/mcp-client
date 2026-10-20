# Build an AI Agent that acts as an MCP Client

An example of how to build an `Agent` that acts as an MCP Client, so that it can connect to external services via MCP. 

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/ai/tree/main/demos/mcp-client)

This demo showcases how to: 
- Connect an AI agent to a remote MCP server
- Handle authentication check using the built-in OAuth flow
- Discover and use tools exposed by remote MCP servers

[Learn more](https://blog.cloudflare.com/building-ai-agents-with-mcp-authn-authz-and-durable-objects/)

## Instructions

First, start an MCP server. A simple example can be found in `examples/mcp`, which already has valid binding setup.

```sh
npm install
npm start
```

Tap "O + enter" to open the front end. It should list out all the tools, prompts, and resources available.

## CI

The `.github/workflows/ci.yml` workflow runs on pull requests and pushes to `main`. It installs dependencies with `npm ci` and runs `npm run type-check` and `npm run build`.

## Dependabot auto-merge

`.github/workflows/dependabot-auto.yml` runs after the `CI` workflow finishes on a Dependabot pull request.

- A patch or minor bump is squash-merged only when `CI` succeeded on that exact head SHA and no other check on the head failed.
- A major bump whose `CI` run failed is closed with a comment, but only while `CI` on the default branch is green; Dependabot treats a closed pull request as ignoring that version.
- A green major bump, a pull request without Dependabot's update-type metadata, and a stale head are left for a human.

The workflow uses `workflow_run` instead of `gh pr merge --auto` because this repository has no required status checks, so `--auto` would merge at once with no gate.
