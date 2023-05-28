---
title: "Nginx Logging"
date: 2023-05-20T11:30:03+06:00
showToc: true
TocOpen: false
draft: false
tags: ["nginx"]
---

Nginx uses a few different directives to control system logging. The one included in the core module is called `error_log`.

# `error_log` directive

Syntax: `error_log log_file log_level`.

- `log_file`: specifies the file where the logs will be written.
- `log_level`: specifies the lowest level of logging to be recorded.

### Logging levels

- `emerg`: emergency situations.
- `alert`:
- `crit`:
- `error`:
- `warn`:
- `notice`:
- `info`
- `debug`:

<ins>Example</ins>:

```bash
error_log /var/log/nginx/error.log crit;

# Don't log anything
error_log /dev/null crit;
```

`error_log` is part of the core module; the `access_log` is part of the `HttpLogModule`. This provides the ability to customise the log.

# `log_format` directive

The `log_format` directive is used to describe the format of a log entry using the plain text and variables.

<ins>General Syntax</ins>:

```bash
log_format format_name string_describing_formatting;
```

```bash
log_format combined '$remote_addr - $remote_user [$time_local]  '
      '"$request" $status $body_bytes_sent '
      '"$http_referer" "$http_user_agent"';
```

> `combined` comes predefined with Nginx.

# `access_log` directive

<ins>Syntax</ins>:

```bash
access_log /path-to-location [ format_of_log buffer_size ];
```

Specify compression of log file by adding `gzip`:

```bash
access_log /path-to-log-location format_of_log gzip;
```

### Managing a log rotation

The command that actually rotates the logs is `kill -USR1 /var/run/nginx.pid`. It sends signal to reload its log files.

### Log rotation with `logrotate`

The `logrotate` application is used to rotate logs.

```bash
vim /etc/logrotate.d/nginx
```
