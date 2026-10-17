# Lab 01 — Your First Network

**Duration:** 30 min
**Goal:** Make two PCs talk through a switch and watch the OSI layers in action.

## Topology

```
        ┌────────┐
        │  PC0   │
        │ .1.10  │
        └───┬────┘
            │ Copper Straight-Through
            │ Fa0/1
     ┌──────┴──────┐
     │   2960 SW   │
     └──────┬──────┘
            │ Copper Straight-Through
            │ Fa0/2
        ┌───┴────┐
        │  PC1   │
        │ .1.11  │
        └────────┘
```

| Device | Interface / Port | IP Address | Subnet Mask |
|--------|------------------|------------|-------------|
| PC0    | NIC              | 192.168.1.10 | 255.255.255.0 |
| PC1    | NIC              | 192.168.1.11 | 255.255.255.0 |
| SW0    | Fa0/1 → PC0      | —          | —           |
| SW0    | Fa0/2 → PC1      | —          | —           |

## Build

1. Add 1 switch (2960) and 2 PCs.
2. Connect with **Copper Straight-Through** cables: PC0 → Fa0/1, PC1 → Fa0/2.
3. Set the IPs (PC > Desktop > IP Configuration):
   - PC0: `192.168.1.10` / `255.255.255.0`
   - PC1: `192.168.1.11` / `255.255.255.0`
4. On PC0, open **Command Prompt** and run:

   ```
   ping 192.168.1.11
   ```

   **Expected:** 4 replies from 192.168.1.11 — the two PCs can talk.

## Investigate

5. Click **Simulation Mode** (bottom right) and run the ping again.
6. Press **Play** and watch the packets move:
   - The first packet is **ARP** — PC0 asks "who has 192.168.1.11?" because it only knows the IP, not yet the MAC address.
   - Then come the **ICMP** echo requests/replies — the actual ping.
7. Click a packet and open the **OSI Model** tab. Find:
   - **Layer 2 (Data Link):** the MAC address (e.g. `00D0.xxxx.xxxx`) — used hop-to-hop between PC and switch.
   - **Layer 3 (Network):** the IP address (`192.168.1.10` → `192.168.1.11`) — used end-to-end.

   The switch only reads layer 2 (it forwards frames by MAC address and builds its MAC address table).
   The PCs use layer 3 to decide whether the destination is on the same subnet.

## Break it on purpose

8. Change PC1 to `192.168.2.11` (mask stays `255.255.255.0`) and ping again.

   **Result:** the ping fails.

### Why it fails

- With mask `255.255.255.0`, PC0 (`192.168.1.10`) computes its network as **192.168.1.0/24** and PC1 (`192.168.2.11`) computes **192.168.2.0/24** — they are now on **different subnets**.
- PC0 compares the destination IP with its own subnet: not on the local network, so it must send through a **default gateway**.
- **No gateway is configured**, so PC0 has nowhere to forward the packet. It never even sends an ARP for PC1 (ARP only resolves addresses on the local subnet), and the ping dies.
- The switch wouldn't help here anyway — a switch forwards frames inside one LAN, it never moves traffic between subnets. That's a router's job.

## Fix it

9. Return PC1 to `192.168.1.11` and the ping works again.

## Files

- `lab-01.pkt` — Packet Tracer topology (final state: both PCs on 192.168.1.0/24, ping working)

## Tools

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
