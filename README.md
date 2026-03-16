# macp-agent-mcp

MCP server that gives AI agents access to the [Multi-Agent Cognition Protocol](https://github.com/multiagentcognition/macp).

Activate it once per project and supported hosts auto-register each session on startup.

## Quick Start

```bash
npx -y macp-agent-mcp init
```

That command:
- derives `projectId` from the current folder by default
- creates `.macp/config.json`
- creates a local SQLite bus under `.macp/`
- writes project-local MCP config for supported hosts
- updates `AGENTS.md` and `CLAUDE.md` with a managed MACP block

Then open Claude Code, OpenCode, Gemini CLI, or another MCP-capable host in that folder. Each session gets its own MCP server process, auto-registers, and joins the MACP workspace.

## Host Support

Project activation writes config for:

- Claude Code: `.mcp.json` + `CLAUDE.md`
- OpenCode: `opencode.json` + `AGENTS.md`
- Gemini CLI: `.gemini/settings.json` + `AGENTS.md`
- Cursor / VS Code: `.cursor/mcp.json` / `.vscode/mcp.json`

## Tool Surface

Core MACP tools:
- `macp_get_instructions`, `macp_register`, `macp_join_channel`
- `macp_send_channel`, `macp_send_direct`, `macp_poll`, `macp_ack`, `macp_deregister`

Optional workspace extensions:
- awareness: `macp_ext_list_agents`, `macp_ext_get_session_context`
- file ownership: `macp_ext_claim_files`, `macp_ext_release_files`, `macp_ext_list_locks`
- memory: `macp_ext_set_memory`, `macp_ext_get_memory`, `macp_ext_search_memory`, `macp_ext_list_memories`, `macp_ext_delete_memory`, `macp_ext_resolve_memory`
- profiles: `macp_ext_register_profile`, `macp_ext_get_profile`, `macp_ext_list_profiles`, `macp_ext_find_profiles`
- goals: `macp_ext_create_goal`, `macp_ext_list_goals`, `macp_ext_get_goal`, `macp_ext_update_goal`, `macp_ext_get_goal_cascade`
- tasks: `macp_ext_dispatch_task`, `macp_ext_claim_task`, `macp_ext_start_task`, `macp_ext_complete_task`, `macp_ext_block_task`, `macp_ext_cancel_task`, `macp_ext_get_task`, `macp_ext_list_tasks`, `macp_ext_archive_tasks`
- lifecycle: `macp_ext_sleep_agent`, `macp_ext_deactivate_agent`, `macp_ext_delete_agent`
- vault/docs: `macp_ext_register_vault`, `macp_ext_search_vault`, `macp_ext_get_vault_doc`, `macp_ext_list_vault_docs`
- context search: `macp_ext_query_context`

## Related

- [macp](https://github.com/multiagentcognition/macp) — the protocol: spec, schema, core logic, and extensions
- [macp-openclaw-plugin](https://github.com/multiagentcognition/macp-openclaw-plugin) — OpenClaw plugin that also exposes MACP coordination

## License

[PolyForm Strict 1.0.0](LICENSE)
