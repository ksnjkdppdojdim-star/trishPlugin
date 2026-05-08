<!-- 
  Copyright (c) 2026 Jules MAHOUNOU
  Project  : TRISH
  Initiated: 17/04/2026
  Origin   : Benin
  Contact  : jtodjinou@datatechnologies.bj | +229 0159521211
  License  : MIT — see LICENSE file for details
-->

# trishPlugin

Example Trish dynamic plugin installed from a Git repository.

## Structure

- `trish-plugin.json`: manifest read by `trish plugin install`.
- `helloGit.ps1`: PowerShell entrypoint executed on the remote Windows agent.

## Install From Git

```powershell
.\trish.exe plugin install https://github.com/ksnjkdppdojdim-star/trishPlugin.git
```

Then verify:

```powershell
.\trish.exe plugin list
.\trish.exe info DESKTOP-0JSGE83
```

You should see the `hello-git` command.

## Run

```powershell
.\trish.exe exec DESKTOP-0JSGE83 hello-git Codex
```

Or from the interactive shell:

```text
trish> use DESKTOP-0JSGE83
trish[DESKTOP-0JSGE83]> hello-git Codex
```

## Update

After pushing a new version to GitHub:

```powershell
.\trish.exe plugin update all
```

Or reinstall/update only this plugin:

```powershell
.\trish.exe plugin update https://github.com/ksnjkdppdojdim-star/trishPlugin.git
```

## Manifest Notes

The command exposed by this plugin is `hello-git`:

```json
{
  "name": "trishPlugin",
  "version": "1.0.0",
  "entry": "helloGit.ps1",
  "shell": "powershell",
  "os": ["windows"],
  "commands": [
    { "name": "hello-git" }
  ]
}
```

Keep plugin files self-contained. Helper files can be placed next to the manifest and loaded from `$PSScriptRoot`.
