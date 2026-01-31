# First Ping Failure – ARP Investigation

## Problem Statement
When pinging a newly connected device, the first ICMP echo request fails while subsequent pings succeed.

## Expected Behavior
ICMP echo requests should succeed immediately.

## Observed Behavior
- First ping fails
- All following pings succeed

## Hypothesis
The failure is caused by Layer 2 address resolution (ARP) before ICMP can be sent.

## Methodology
- Cleared ARP cache
- Captured traffic using Wireshark
- Repeated tests with freshly connected devices

## Analysis
The first packet observed is an ARP request. The ICMP packet is only sent after the ARP reply is received, which explains the initial timeout.

## Conclusion
The first ping fails due to ARP resolution delay. Once the MAC address is known, ICMP traffic flows normally.

