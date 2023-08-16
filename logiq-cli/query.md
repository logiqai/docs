---
description: This page documents command-line usage for the Query command
---

# Query

## Help

```text
NAME:
   logiqctl query - query "sudo cron" 2h

USAGE:
   logiqctl query command [command options] [application names, relative time]

COMMANDS:
   next, n  query n
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --end_time value, --et value    Relative end time. (default: "10h")
   --filter value, -f value        Filter expression e.g. 'Hostname=127.0.0.1,10.231.253.255;Message=tito*'
   --output value, -o value        Set output format to be column|json|raw (default: "column")
   --start_time value, --st value  Relative start time. (default: "10h")
   --tail, -t                      Tail the data without paginating (default: false)
   --help, -h                      show help (default: false)
   --version, -v                   print the version (default: false)
```

## Historical queries

Historical log data can be queries using apicactl. Filters allow the user to specify a time range, filter criteria like application name, matching patterns etc.

For e.g. to query all postgres logs within the last 1 hr, one would pass the application names and the start time for the query

```text
$logiqctl q postgres --st 1h
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       superuser. For example, "-e POSTGRES_PASSWORD=password" on "docker run".
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|Error: Database is uninitialized and superuser password is not specified.
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       You may also use "POSTGRES_HOST_AUTH_METHOD=trust" to allow all
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       https://www.postgresql.org/docs/current/auth-trust.html
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       connections without a password. This is *not* recommended.
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       You must specify POSTGRES_PASSWORD to a non-empty value for the
2020-03-17T03:52:36Z        |error |docker-desktop|1518|postgres|system daemon|       See PostgreSQL documentation about "trust":
Enter `n` or `next' to continue.
```

## Output formatting

The query output formatting can be controlled with the `--output` option. Three values are allowed - `raw`, `column` and `json`

```text
$logiqctl q postgres --st 1h --output json
```

The above command returns the data with each row of data formatted as JSON.

