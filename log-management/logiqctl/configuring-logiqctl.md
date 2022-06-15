---
description: This page covers installation and configuration of logiqctl
---

# Configuring logiqctl

## Installation

The simplest way to try `logiqctl` is to download a pre-built binary from the [release](https://github.com/logiqai/logiqctl/releases) page. You can also build the binaries directly from source. Instructions are available [here](https://github.com/logiqai/logiqctl#how-to-build-from-source).

### Configuring `logiqctl`&#x20;

`logiqctl` requires a running Logiq cluster and an api key. See how to get the API key [here](obtaining-api-key.md). After obtaining the API key, run the below commands to configure the logiqctl.

```
# Set cluster end point
> logiqctl config set-cluster your-logiq-cluster.com

# Set the API Key
> logiqctl config set-token r0q7EyIxNgVjAqLoIeDioJAWEhAR6wK4Y5XpPb3A

# Set the default namespace 
> logiqctl config set-context ngnix
```

The default namespace settings can be overridden by passing `-n` flag. Basic operations are covered below, for more detailed documentation refer to the [user guide](https://logiqctl.logiq.ai/) for `logiqctl`.&#x20;

### `logiqctl` logs

The `logs` command is used to view historical logs. The command supports an `interactive` mode as well which lets the user select application and process.&#x20;

[![asciicast](https://asciinema.org/a/353013.svg)](https://asciinema.org/a/353013)

### `logiqctl` tail

The tail command can be used to view the logs from applications in realtime. The tail command runs an interactive prompt and lets the user choose the application and processes.&#x20;

[![asciicast](https://asciinema.org/a/353019.svg)](https://asciinema.org/a/353019)
