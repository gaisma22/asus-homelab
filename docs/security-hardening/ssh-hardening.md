# SSH Hardening

## Configuration File
`/etc/ssh/sshd_config`

## Changes Made

### PermitRootLogin no
Root account cannot log in via SSH directly.
Even if someone knows the root password, SSH rejects the connection.
All admin work goes through `gaisma22-server` with `sudo`.

### PermitEmptyPasswords no
Accounts with no password cannot authenticate via SSH.
Prevents accidental access through misconfigured accounts.

### AllowUsers gaisma22-server
Only `gaisma22-server` is permitted to connect via SSH.
Any other account on the system is blocked at the SSH level
regardless of whether they have valid credentials.

## Pending
### PasswordAuthentication no
Left commented out intentionally. Will be disabled after SSH
key authentication is confirmed working. Disabling passwords
before keys are set up would lock out remote access completely.

## Applied With
`sudo systemctl restart sshd`

## Verified
`sudo systemctl status sshd` — active (running)
