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

## Lab convention

Each lab folder contains:

- `README.md` — objective, topology explanation, and steps
- `<lab>.pkt` — the Packet Tracer topology file
- `topology.png` — exported diagram image
- `configs/` — device running-configurations per device

## Tools

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
