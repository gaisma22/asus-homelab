# fail2ban Configuration

## Purpose
Watches `auth.log` for repeated failed login attempts and
automatically bans offending IP addresses via `ufw`.

## How It Works
1. Monitors `/var/log/auth.log` using kernel inotify
2. Matches lines against regex filters per service
3. Counts failures per IP within the time window
4. When threshold hit, runs `ufw insert 1 deny from IP`
5. Removes ban automatically when bantime expires

## Configuration File
`/etc/fail2ban/jail.local` — never edited `jail.conf` directly
as it gets overwritten on package updates.

## Settings
- `bantime = 1h` — banned IPs blocked for 1 hour
- `findtime = 10m` — failure window is 10 minutes
- `maxretry = 5` — 5 failures triggers a ban
- `bantime.increment = true` — bans get progressively longer
- `bantime.multiplier = 2` — each repeat ban doubles in length

## Active Jails
- `sshd` — watching port `22` for SSH failures

## Useful Commands
- `sudo fail2ban-client status` — list all active jails
- `sudo fail2ban-client status sshd` — SSH jail details
- `sudo fail2ban-client set sshd unbanip X.X.X.X` — manual unban

## Adding Future Jails
When new services are installed, add a section to `jail.local`
with `enabled = true`. Filters and log paths are pre-written
in `jail.conf` for most common services.
