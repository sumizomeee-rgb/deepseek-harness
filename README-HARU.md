# Haru's DeepSeek Harness setup

This fork runs the upstream Harness with the independent
[`@sumizomeee/dsh-haru-theme`](https://github.com/sumizomeee-rgb/dsh-haru-theme)
client plugin. The plugin is a Git submodule under `packages/client/ui-haru-theme`.
The fork's `haru-custom` branch tracks the desired upstream features; the
`upstream` Git remote points to `deepseek-ai/deepseek-harness`.

## First setup and updates

```powershell
git submodule update --init --recursive
corepack pnpm@11.7.0 install --frozen-lockfile
corepack pnpm@11.7.0 run build
```

Start from this checkout's directory:

```powershell
$env:DSH_HOME = 'E:\Such_Proj\Other\DeepSeekHarness\.local'
$env:DSH_TELEMETRY_DISABLED = '1'
corepack pnpm@11.7.0 dsh web
```

The Web app runs at `http://127.0.0.1:3080/`. Open the launch URL printed by
the CLI for a fresh browser; it exchanges a one-use token for a local cookie.
The `.local` directory contains private credentials, profiles, session history,
and logs. It is outside both public Git repositories.

The current local profile uses CC Switch's Anthropic Messages gateway at
`127.0.0.1:15721`. The three model IDs are `deepseek-v4.1-flash`,
`glm-5.3-flash`, and `qwen3.8-max`. The profile and credential file are
machine-specific; clone the code and configure the target machine's own API
secret separately.

The built-in Web interface can launch a session against any registered
workspace and export that session's log from its header menu. Headless and SDK
profiles are also available through the same `dsh` CLI, but this machine's
custom model route is currently configured only for the Web profile.
