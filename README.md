# Day 02 - Router Between Two Networks

## 목표

라우터를 사용해 서로 다른 두 네트워크를 통신시킨다.

- 192.168.10.0/24
- 192.168.20.0/24

## 토폴로지

PC0 ─ Switch0 ─ Router1 ─ Switch1 ─ PC1

## IP Addressing

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| PC0 | Fa0 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| Router1 | G0/0 | 192.168.10.1 | 255.255.255.0 | - |
| Router1 | G0/1 | 192.168.20.1 | 255.255.255.0 | - |
| PC1 | Fa0 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |

## Router Configuration

```bash
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

end
write memory
