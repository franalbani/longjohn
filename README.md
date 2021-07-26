# longjohn

Docker-compose networking example for ilustrating [this stackoverflow question](https://stackoverflow.com/questions/67013137/in-docker-compose-why-container-connected-to-bridge-a-can-ping-bridge-b).

# Results

```
$ docker-compose up
Recreating longjohn_jim_1 ... done
Recreating longjohn_ben_1 ... done
Attaching to longjohn_ben_1, longjohn_jim_1
jim_1  | 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
jim_1  |     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
jim_1  |     inet 127.0.0.1/8 scope host lo
jim_1  |        valid_lft forever preferred_lft forever
jim_1  | 240: eth0@if241: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue state UP 
jim_1  |     link/ether 02:42:ac:10:14:02 brd ff:ff:ff:ff:ff:ff
jim_1  |     inet 172.16.20.2/24 brd 172.16.20.255 scope global eth0
jim_1  |        valid_lft forever preferred_lft forever
jim_1  | default via 172.16.20.1 dev eth0 
jim_1  | 172.16.20.0/24 dev eth0 scope link  src 172.16.20.2 
jim_1  | PING 172.16.21.1 (172.16.21.1): 56 data bytes
jim_1  | 64 bytes from 172.16.21.1: seq=0 ttl=64 time=0.158 ms
jim_1  | 64 bytes from 172.16.21.1: seq=1 ttl=64 time=0.107 ms
ben_1  | 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
ben_1  |     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
ben_1  |     inet 127.0.0.1/8 scope host lo
ben_1  |        valid_lft forever preferred_lft forever
ben_1  | 238: eth0@if239: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue state UP 
ben_1  |     link/ether 02:42:ac:10:15:02 brd ff:ff:ff:ff:ff:ff
ben_1  |     inet 172.16.21.2/24 brd 172.16.21.255 scope global eth0
ben_1  |        valid_lft forever preferred_lft forever
ben_1  | default via 172.16.21.1 dev eth0 
ben_1  | 172.16.21.0/24 dev eth0 scope link  src 172.16.21.2 
ben_1  | PING 172.16.20.1 (172.16.20.1): 56 data bytes
ben_1  | 64 bytes from 172.16.20.1: seq=0 ttl=64 time=0.161 ms
jim_1  | 64 bytes from 172.16.21.1: seq=2 ttl=64 time=0.069 ms
jim_1  | 
jim_1  | --- 172.16.21.1 ping statistics ---
jim_1  | 3 packets transmitted, 3 packets received, 0% packet loss
jim_1  | round-trip min/avg/max = 0.069/0.111/0.158 ms
jim_1  | PING 172.16.21.2 (172.16.21.2): 56 data bytes
ben_1  | 64 bytes from 172.16.20.1: seq=1 ttl=64 time=0.073 ms
ben_1  | 64 bytes from 172.16.20.1: seq=2 ttl=64 time=0.085 ms
ben_1  | 
ben_1  | --- 172.16.20.1 ping statistics ---
ben_1  | 3 packets transmitted, 3 packets received, 0% packet loss
ben_1  | round-trip min/avg/max = 0.073/0.106/0.161 ms
ben_1  | PING 172.16.20.2 (172.16.20.2): 56 data bytes
jim_1  | 
jim_1  | --- 172.16.21.2 ping statistics ---
jim_1  | 3 packets transmitted, 0 packets received, 100% packet loss
longjohn_jim_1 exited with code 1
ben_1  | 
ben_1  | --- 172.16.20.2 ping statistics ---
ben_1  | 3 packets transmitted, 0 packets received, 100% packet loss
longjohn_ben_1 exited with code 1
```
