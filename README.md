# ARP Spoof

Simple Python ARP spoofing script I put together while going through a hacking/programming course. Uses Scapy to poison ARP tables so you can sit in the middle of traffic between a target and the gateway.

## What it does

- Sends fake ARP replies telling the target that you are the gateway
- Tells the gateway that you are the target
- Keeps the tables poisoned by sending the packets every 2 seconds
- Counts how many packets you’ve fired

Hard-coded IPs in the loop are for a VirtualBox lab setup (10.0.2.7 target, 10.0.2.1 gateway). Change them to whatever you’re testing on.

## Requirements

```bash
pip install scapy
```

Run it as root (or with sudo) because raw packet crafting needs privileges.

## Usage

```bash
sudo python3 arp_spoof.py
```

Hit Ctrl+C when you’re done. The script just quits; it doesn’t restore the original ARP entries. If you want clean tables again, reboot the machines or send proper restore packets yourself.

## Notes

This is for lab / educational use only. Pointing it at machines you don’t own or don’t have permission to test is illegal and a quick way to get in trouble.

Made while following along with a Udemy-style course on writing hacking tools in Python. Nothing fancy, just the core loop that gets the job done.
