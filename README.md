# Unbound DNS

Ansible playbook to configure [Unbound](https://nlnetlabs.nl/projects/unbound/about/) as a recursive DNS server for PiHole to use.

For details, see: https://docs.pi-hole.net/guides/dns/unbound/

This playbook is intended to supplement Jeff Geerling's Internet Pi playbook.
See: [`geerlingguy/internet-pi`](https://github.com/geerlingguy/internet-pi)

## Requirements

* A Raspberry Pi running PiHole
* Access to your PiHole admin panel

## Setup

Modify `inventory.ini` with your pi's IP address (or specify `connection=local`).

If desired, you can change any part of the Unbound configuration by specifying values in `override.yml`.
See `defaults.yml` for details.

## Usage

Log in to your PiHole admin panel and go to the Settings/DNS page.
<!-- Untick any upstream DNS servers and add `127.0.0.1#5335` and `::1#5335` as upstream DNS servers. -->
Untick any upstream DNS servers and add `127.0.0.1#5335` as an upstream DNS server.

If you are running PiHole in a Docker container, you may instead want to specify the the NAT address for your host available to the container (i.e., a `172.16.0.0/12` address).

Additionally, you may want to create `/etc/dnsmasq.d/99-edns.conf` inside that container:
```
edns-packet-max=1232
```
Unbound is already configured to use this limit.
Adding this file to the PiHole container signals FTL to also abide by this limit.

Now, you're running your own private recursive DNS server on your PiHole. :tada: :tada:
