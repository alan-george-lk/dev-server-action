# LiveKit Dev Server Action

[![CI](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml/badge.svg)](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml)

Install and run a LiveKit server in development mode for end-to-end testing.

## Usage

```yaml
- uses: livekit/dev-server-action@v1
  with:
    github-token: ${{ github.token }}
```

Pin a specific server release or commit (builds from source when no binary is
available for the runner OS, e.g. macOS or a commit SHA):

```yaml
- uses: livekit/dev-server-action@v1
  with:
    github-token: ${{ github.token }}
    version: a47e21b6cb945aabee88c98650366cef8cbf7a99
    config: |
      enable_data_tracks: true
      enable_participant_data_blob: true
```

## Inputs

| Name           | Required | Default | Description                                                          |
| -------------- | -------- | ------- | -------------------------------------------------------------------- |
| `github-token` | Yes      |         | Token used to download the LiveKit server release.                   |
| `version`      | No       | `""`    | Release tag (e.g. `v1.13.2`) or `livekit/livekit` commit SHA. When empty, Linux and Windows use the latest release; macOS uses Homebrew. |
| `config`       | No       | `""`    | Server configuration YAML merged over the action base config.        |

## Outputs

| Name       | Description                       |
| ---------- | --------------------------------- |
| `pid`      | Process ID of the running server. |
| `log-path` | Path to the server log file.      |
