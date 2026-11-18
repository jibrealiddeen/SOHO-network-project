# Small Office / Home Office Network

_Level: foundation — Enterprise Campus & LAN — Static Addressing · Default Route · DHCP · Switching_

**Status: Verified.** Completed on 2026-11-18; every requirement was machine-checked against the network built in BuildTheNet and passed.

Snapshot taken 2026-11-18. Built in a simulation — no physical or production equipment was involved.

## Scenario

Hollis & Fane, a two-person bookkeeping practice, is moving into a converted shop with a fibre line and no network. Give them the smallest network that works: one router, one switch, the two staff PCs, addresses handed out automatically, and a route to the internet.

### Why it matters

Every larger design is this one repeated. Getting a gateway, a subnet and a default route right for a client who just wants their PCs online is what makes the next twenty projects readable.

## Requirements

| # | Requirement | Status | Checked by |
|---|---|---|---|
| 1 | Place a router, a switch and at least two PCs, cabled into one LAN. | Passed | Sandbox check |
| 2 | Address the LAN from a single /24 and give the router the first usable address. | Passed | Sandbox check |
| 3 | Hand out host addresses from a DHCP pool on the router, excluding the gateway. | Passed | Sandbox check |
| 4 | Give the router a default route toward the ISP. | Passed | Sandbox check |

## Topology

![Topology diagram](topology.svg)

## Addressing

| Device | Interface | Address | Mask | Mode | Gateway |
|---|---|---|---|---|---|
| R1 | Gi0/0 | 192.168.1.1/24 | 255.255.255.0 | routed |  |
| R1 | Gi0/1 | 203.0.113.2/24 | 255.255.255.0 | routed |  |
| ISP-Cloud-1 | Gi0/0 | 203.0.113.1/24 | 255.255.255.0 | routed |  |
| ISP-Cloud-1 | Gi0/1 | 198.51.100.1/24 | 255.255.255.0 | routed |  |

## Device configurations

Running-configs as `show running-config` prints them in the BuildTheNet sandbox. Passwords, secrets, keys and SNMP communities are replaced with `<removed>`.

- [R1](configs/R1.txt)
- [S1](configs/S1.txt)

---

Built on [BuildTheNet](https://www.buildthenet.io/projects/proj-pt-01-soho)
