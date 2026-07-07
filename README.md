# LiveKit Dev Server Action

[![CI](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml/badge.svg)](https://github.com/livekit/dev-server-action/actions/workflows/ci.yml)

Install and run a LiveKit server in development mode for end-to-end testing.

## Usage

> Note: replace `<sha>` with pinned action or server commit SHA.

```yaml
- uses: livekit/dev-server-action@<sha>
  with:
    github-token: ${{ github.token }}
```

Pin a release tag or commit from [livekit/livekit](https://github.com/livekit/livekit):

```yaml
- uses: livekit/dev-server-action@<sha>
  with:
    github-token: ${{ github.token }}
    version: v1.13.3
```

Build from a specific commit:

```yaml
- uses: livekit/dev-server-action@<sha>
  with:
    github-token: ${{ github.token }}
    version: <sha>
    config: |
      logging:
        level: debug
```

Pass in [config parameters](https://github.com/livekit/livekit/blob/master/config-sample.yaml) to further test specific features:

```yaml
- uses: livekit/dev-server-action@<sha>
  with:
    github-token: ${{ github.token }}
    version: <sha>
    config: |
      logging:
        level: debug
```

## Inputs

| Name           | Required | Default  | Description                                                                        |
| ---------------| ---------| ---------| -----------------------------------------------------------------------------------|
| `github-token` | Yes      |          | Token used to download releases or resolve the latest tag.                         |
| `version`      | No       | `latest` | Server version: `latest`, release tag (`v1.13.3` or `1.13.3`), or commit SHA.      |
| `config`       | No       | `""`     | Server configuration YAML merged over the action's base dev config.                |

Linux and Windows download release artifacts for tags. Commit SHAs and pinned tags on
macOS build from source. `latest` on macOS uses Homebrew.

## Outputs

| Name       | Description                       |
| ---------- | --------------------------------- |
| `pid`      | Process ID of the running server. |
| `log-path` | Path to the server log file.      |
