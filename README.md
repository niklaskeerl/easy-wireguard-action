# Easy WireGuard Connection

This GitHub Action simplifies the setup of a WireGuard connection using `wg-quick`. It only requires a WireGuard configuration file as input to get your connection up and running quickly. No more multiple input variables or complex setup!

The action uses the `wg0` interface and writes its configuration to
`/etc/wireguard/wg0.conf`, owned by root with permissions `600`. The configuration
is not printed to the log. Using the standard configuration directory also avoids
workspace file access restrictions in the `wg-quick` AppArmor profile on Ubuntu
26.04.

## Usage

To use this GitHub Action, follow these steps in your workflow file:

```yaml
name: Set up WireGuard Connection

on:
  push:
    branches:
      - main

jobs:
  wireguard:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Set up WireGuard Connection
      uses: niklaskeerl/easy-wireguard-action@v3
      with:
        WG_CONFIG_FILE: ${{ secrets.WG_CONFIG_FILE }}
```
