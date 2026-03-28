# Firewall Configuration

## Tool
`ufw` (Uncomplicated Firewall)

## Default Policies
- Incoming: `deny` — all ports blocked unless explicitly opened
- Outgoing: `allow` — server can make outgoing connections freely
- Routed: `disabled` — this server does not forward traffic

## Open Ports
- `22/tcp` — SSH (IPv4)
- `22/tcp (v6)` — SSH (IPv6)

## Commands Used
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw enable
```

## Why Only Port 22
A server should expose the minimum surface area possible.
Every open port is a potential attack vector. We open only
what is needed and nothing else. Additional ports will be
opened only when a specific service requires it.
