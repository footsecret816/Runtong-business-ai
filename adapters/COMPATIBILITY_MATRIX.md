# Platform Compatibility Matrix

Verified against public official documentation on **2026-09-08**. Platform behavior and file conventions can change; re-verify when implementing or upgrading an adapter.

## Interpretation

- **Business-core compatibility** asks whether the platform can consume the same Kernel / Skills / Cases / Knowledge / Memory methodology.
- **Deployment compatibility** asks how much platform-specific packaging is required.
- A high compatibility rating does **not** mean the model has passed the Runtong Business AI Evals.

| Platform | Native instruction / context mechanism | Skills / extensions | Tool / integration model | V1 adapter status | Compatibility assessment |
|---|---|---|---|---|---|
| **Codex** | Repository `AGENTS.md` can provide persistent project instructions and scope | Canonical repo skills can be referenced from the agent entry; platform-specific packaging can remain thin | Depends on the active Codex environment and connected tools | `adapters/codex/` exists | **High** — strong repository-native fit |
| **Claude Code** | `CLAUDE.md` is always-on project context; nested files can load by scope | Native Skills use `SKILL.md`; plugins can package Skills, Agents, Hooks and MCP | MCP, hooks, built-in tools and subagents are supported | Not yet implemented | **High** — very close conceptual match; native skill packaging is available |
| **DeepSeek Harness** | Harness configuration composes the runtime rather than relying on one canonical markdown entry | Models, tools, skills, sessions, storage, loops, scheduling and UI are plugin capabilities | Plugin-based; local-first runtime with configurable external services/tools | Not yet implemented | **High** — excellent architectural fit, but currently developer preview and interfaces may evolve |
| **WorkBuddy / CodeBuddy** | Workspace/project configuration plus plugin/agent instructions | Native Skills use `SKILL.md`; plugins can include Skills, Agents, Hooks, MCP and LSP components | MCP and plugin components are supported | Not yet implemented | **High** — canonical skills can be repackaged with relatively little business-logic change |
| **Accio Work** | Agent Core uses files such as `MEMORY.md`, `USER.md`, `BOOTSTRAP.md`, `TOOLS.md` and private skill space | Local/custom Skills are supported; agent-private/account/built-in skill tiers exist | Browser/web/file tools, MCP, external integrations and automations are available depending on configuration | Not yet implemented | **Medium-High / High** — business logic maps well, but deployment is more likely to require Agent-Core/Skill packaging rather than a repository `AGENTS.md` boot |
| **Unknown / future platform** | Varies | Varies | Varies | `adapters/generic/` exists | **Conditional** — use Generic Adapter first, then implement native packaging only if the platform proves useful |

## Recommended implementation order

Do **not** build every native adapter in advance.

Implement an adapter when the platform is actually going to be used:

1. inspect current official platform conventions;
2. map the canonical Runtime / Kernel / Skills / Company Pack;
3. map available tools and memory;
4. add only the minimum platform-native files;
5. run canonical Evals and E2E acceptance;
6. mark A4 only after passing.

## Canonical behavior that must remain identical across platforms

Regardless of platform, preserve:

- fact vs inference discipline;
- active-project source precedence;
- strategy-before-writing for complex conflicts;
- selective skill routing;
- simple-task minimum-depth behavior;
- commercial authorization boundaries;
- Company Pack vs project-specific scope;
- case-as-reference-not-evidence rule;
- privacy separation of real Customer Memory;
- critical-fail evaluation rules.

## Platform-specific differences that are acceptable

The following may differ without changing the business methodology:

- native entry filename;
- skill directory and metadata syntax;
- MCP/tool configuration format;
- permissions / hooks implementation;
- memory-storage implementation;
- model choice;
- exact wording and prose style within the accepted business-writing standard.

## Official references checked

- OpenAI Codex — AGENTS.md / persistent repository context: https://openai.com/index/introducing-codex/ and https://openai.com/business/guides-and-resources/how-openai-uses-codex/
- Claude Code — extension model, CLAUDE.md, Skills, MCP, Hooks, Plugins: https://code.claude.com/docs/en/features-overview and https://code.claude.com/docs/en/plugins-reference
- DeepSeek Harness — plugin-based Harness architecture: https://www.deepseek.com/harness/en/
- WorkBuddy / CodeBuddy — Skills / Plugins / MCP: https://www.workbuddy.ai/docs/zh/ide/Features/Skills and https://www.workbuddy.ai/docs/zh/cli/plugins-reference
- Accio Work — Agent Core / Skills / Tools: https://www.accio.com/work/doc?slug=agent-core-design , https://www.accio.com/work/doc?slug=skills-guide and https://www.accio.com/work/doc?slug=agent-tools-guide
