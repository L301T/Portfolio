# Project Description

Design and simulation of a network infrastructure for a small expanding company, consisting of a main office (Red LAN) and a branch office (Green LAN), interconnected through a simulated WAN link.

The topology was created using Cisco Packet Tracer with the goal of ensuring:

- Internal communication within the same office (local intranet).
- Reliable communication between the two offices, including access to network services (e.g., servers) from any endpoint.

## Main Components

- Router for each office with IP configuration and static routing.
- Switches to segment the local network and optimize traffic distribution.
- Centralized server located at the main office (shared services).
- Network printers for both offices.
- Simulated WAN link connecting the routers.

## IP Configuration

- Main office: `192.168.1.0/24`
- Branch office: `192.168.2.0/24`
- WAN link: point-to-point network `192.168.12.0/30`

## Test Results

- Successful ping between devices in both offices (e.g., `192.168.1.3 → 192.168.2.2`).
- No packet loss, average response times under 5 ms.

## Demonstrated Skills

- Network topology design.
- Router and switch configuration using Packet Tracer.
- Subnetting management and static routing.
- Testing and troubleshooting with diagnostic tools (Ping).
