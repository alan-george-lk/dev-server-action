# LiveKit Dev Server Action

[![CI](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml/badge.svg)](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml)

Install and run a LiveKit server in development mode for end-to-end testing.

## Usage

```yaml
- uses: livekit/dev-server-action@v1
  with:
    github-token: ${{ github.token }}
```

## Inputs

| Name           | Required | Default | Description                                                          |
| -------------- | -------- | ------- | -------------------------------------------------------------------- |
| `github-token` | Yes      |         | Token used to download the LiveKit server release.                   |
| `config`       | No       | `""`    | Server configuration YAML

## Outputs

| Name       | Description                       |
| ---------- | --------------------------------- |
| `pid`      | Process ID of the running server. |
| `log-path` | Path to the server log file.      |
