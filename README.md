# Networking Labs

A collection of hands-on networking labs built with Cisco Packet Tracer.
Each lab lives in its own folder and includes the topology file, a diagram,
and the device configurations.

## Structure

```
networking-labs/
├── README.md              (index of all labs)
├── lab-01-first-network/
│   ├── README.md
│   ├── lab-01.pkt
│   ├── topology.png
│   └── configs/
├── lab-02-routing/
└── ...
```

## Labs

| Lab | Title | Topics | Folder |
|-----|-------|--------|--------|
| 00  | Setup | Packet Tracer environment setup | [lab-00-setup](lab-00-setup) |
| 01  | First Network | Switching, ARP, ICMP, OSI model, subnets | [lab-01-first-network](lab-01-first-network) |
| 02  | Router | Routing, default gateway, ARP across hops, TTL | [lab-02-router](lab-02-router) |
| 03  | VLANs | VLAN segmentation, broadcast domains, isolation | [lab-03-vlans](lab-03-vlans) |
| 04  | Inter-VLAN Routing | Trunks, 802.1Q, subinterfaces, router-on-a-stick | [lab-04-inter-vlan-routing](lab-04-inter-vlan-routing) |
| 05  | ACLs | Extended ACLs, wildcard masks, first-match, interface direction | [lab-05-acls](lab-05-acls) |
| 06  | DHCP, DNS, HTTP | DORA, name resolution, web server, APIPA | [lab-06-dhcp-dns-http](lab-06-dhcp-dns-http) |
| 07  | Port Security | Sticky MAC, violation shutdown, black hole VLAN, rogue device | [lab-07-port-security](lab-07-port-security) |
| 08  | DHCP Snooping | Rogue DHCP, trusted/untrusted ports, binding table, rate limit | [lab-08-dhcp-snooping](lab-08-dhcp-snooping) |

## Lab convention

Each lab folder contains:

- `README.md` — objective, topology explanation, and steps
- `<lab>.pkt` — the Packet Tracer topology file
- `topology.png` — exported diagram image
- `configs/` — device running-configurations per device

## Tools

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
