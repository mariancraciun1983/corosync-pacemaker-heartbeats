<h1 align="center">Pacemaker raw_command resource agent</h1>
<br />

<div align="center">
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License" />
  </a>
</div>
<br />

## Introduction

This pacemaker resource agent is useful if you have a resource that can be started/stopped and monitored using linux commands.


## Example

An example would be to block a specific with iptables
```bash
pcs resource create PostgresLBWriteBlock ocf:heartbeat:command_raw \
  start_cmd="/usr/sbin/iptables -A INPUT -p tcp --dport 80 -j REJECT" \
  stop_cmd="/usr/sbin/iptables -D INPUT -p tcp --dport 80 -j REJECT" \
  monitor_cmd="/usr/sbin/iptables -C INPUT -p tcp --dport 80 -j REJECT" \
```

## License
MIT License