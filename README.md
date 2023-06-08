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

## Usage

Log in to your PiHole admin panel and go to the Settings/DNS page.
<!-- Untick any upstream DNS servers and add `127.0.0.1#5335` and `::1#5335` as upstream DNS servers. -->
Untick any upstream DNS servers and add `127.0.0.1#5335` as an upstream DNS server.

Now, you're running your own private recursive DNS server on your PiHole. :tada: :tada:
