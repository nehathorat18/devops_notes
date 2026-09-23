## Linux Troubleshooting Quick Reference

| Problem | Commands |
|---|---|
| CPU High | `top`, `ps aux --sort=-%cpu` |
| Memory High | `free -h`, `ps aux --sort=-%mem` |
| Disk Full | `df -h`, `du -sh` |
| Disk I/O | `iostat`, `vmstat` |
| Process | `ps`, `pgrep`, `top` |
| Service | `systemctl status` |
| Service Logs | `journalctl -u` |
| Port | `ss -tulpn` |
| Network | `ping`, `curl`, `nc` |
| DNS | `nslookup`, `dig` |
| Permissions | `ls -l`, `chmod`, `chown` |


find [where-to-search] [criteria] [action] 

find /var/log/myapp -name "*.log" -mtime +30 -exec rm -f {} \;
find /var/www/html -type d -exec chmod 755 {} \;
find /home/neha/projects -name "*.tar" -exec gzip {} \;
