---
description: This page covers installation and configuration of logiqctl
---

# Configuring logiqctl

## Installation

The simplest way to try `logiqctl` is to download a pre-built binary from [release](https://github.com/logiqai/logiqctl/releases) page. You can also build the binaries directly from source. Instructions are available [here](https://github.com/logiqai/logiqctl#how-to-build-from-source).

### Configuring `logiqctl` 

`logiqctl` require a running Logiq cluster and api key for the user access. See how to generate API key [here](obtaining-api-key.md). After obtaining the API key run the below commands to configure the logiqctl.

```text
# Set cluster end point
> logiqctl config set-cluster your-logiq-cluster.com

# Set the API Key
> logiqctl config set-token r0q7EyIxNgVjAqLoIeDioJAWEhAR6wK4Y5XpPb3A

# Set the default namespace 
> logiqctl config set-context ngnix
```

The default namespace settings can be overridden by passing `-n` flag. Basic operations are covered below, for more detailed documentation see [docs](https://logiqctl.logiq.ai/) for `logiqctl`. 

### `logiqctl` logs

The `logs` command is used to view historical logs. The `logs` command support an `interactive` mode which let user select application and process. 





