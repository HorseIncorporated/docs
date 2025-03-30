# setup

## setting up your codespace for the first time

### add the following variables to your repository secrets

- GITHUB_TOKEN (create a classic github personal access token and paste it as the value)
- ANTHROPIC_API_KEY

### navigate to the workspaces repository

[HorseIncorporated workspace](https://github.com/HorseIncorporated/workspace)

![alt text](<Arc _2025-03-30 at 00.57.46@2x.png>)

create codespace on main

![alt text](<Arc _2025-03-30 at 00.58.12@2x.png>)

### install claude code cli tool

```shell
npm install -g @anthropic-ai/claude-code
```

### do a git pull origin from the root directory

```shell
git pull origin
# this should force you to verify your fingerprint
```

### run setup.sh inside the container

```shell
# clone repositories and push our config updates to all repos
./setup.sh
```

### make sure claude is functional

```shell
devcontainer exec --workspace-folder . claude -p "why is the sky blue?"  --dangerously-skip-permissions
```

## dispatch

**note:** make sure your codespace is stopped before running this

manually dispatch the github action, with the following config
