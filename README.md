# college-of-engineering-campus-network
Complete, enterprise-grade campus network topology for college of engineering slahadin university designed in Cisco Packet Tracer. Features hierarchical design, VLAN segmentation, inter-VLAN routing, OSPF, EtherChannel, FHRP redundancy, and secure edge access.

# College of Engineering Campus Network

A full campus network for the College of Engineering, designed and built in Cisco Packet Tracer, using a 3-layer hierarchical architecture (core → distribution → access).

## Architecture

- **Core layer** — two multilayer switches, each dual-homed to every distribution switch for redundancy
  - `Multilayer Switch1`, `Multilayer Switch0`
  - Core-to-distribution links use point-to-point /30 subnets (e.g. `10.0.0.0/30`, `10.0.0.4/30`)
- **Distribution layer** — one distribution switch per building/cluster
  - `SDSW1` — Software & Informatics dept + Architecture dept
  - `ADSW1` — Earth Lab / "korek lab" building (labs + server room + HQ)
  - (more to be added as remaining buildings are built)
- **Access layer** — per-lab/HQ access switches, each tied to a VLAN

## VLAN / IP Scheme

### SDSW1 building (Software & Informatics + Architecture)

| VLAN | Purpose               | Subnet           |
|------|-----------------------|-------------------|
| 99   | Management            | 192.168.99.0/29  |
| 2    | Lab 2 (30 computers)   | 192.168.1.64/27  |
| 3    | Lab 3 (40 computers)   | 192.168.1.0/26   |
| 4    | Software HQ (15)       | 192.168.1.96/27  |
| 5    | Huawei Lab (25)        | 192.168.1.128/27 |
| 6    | Architecture HQ (20)   | 192.168.1.160/27 |

### ADSW1 building (korek lab)

| VLAN | Purpose                                  | Subnet            |
|------|-------------------------------------------|--------------------|
| —    | Management                                | 192.168.99.8/29   |
| 6    | LAB 1 (30 computers)                      | 192.168.2.0/27    |
| 7    | LAB 2 (40 computers)                      | 192.168.2.64/26   |
| 8    | Server room (DHCP, WWW, DNS servers)      | 192.168.3.0/24    |
| 9    | korek HQ (10 computers)                   | 192.168.2.128/28  |

> Note: VLAN 6 is reused across the two buildings for different purposes. Not a conflict since they're separate distribution domains, but worth reviewing for consistency once all buildings are added.

## Repository Structure

```
packet-tracer/   Cisco Packet Tracer .pkt file(s)
docs/            Diagrams (hand-drawn + Packet Tracer screenshots), notes
configs/         Exported device configs (show running-config output)
```

## Status

- [x] Initial topology designed
- [x] Core layer + 2 buildings built (Software & Informatics, Architecture, korek lab)
- [ ] Remaining buildings: Mechanical, Electrical, Chemical/Petrochemical, Civil, Dept. of Civil Engineering, Surveying, Library
- [ ] Router + ISP/internet edge
- [ ] Full VLAN numbering plan across all buildings
- [ ] Device configs exported and documented

## Author

Ayub — Software Engineering student, working toward CCNA/RHCSA-aligned networking and sysadmin skills.