# Easy WireGuard Connection

This GitHub Action simplifies the setup of a WireGuard connection using `wg-quick`. It only requires a WireGuard configuration file as input to get your connection up and running quickly. No more multiple input variables or complex setup!

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
      uses: niklaskeerl/wireguard-quick-setup-action@v1
      with:
        WG_CONFIG_FILE: ${{ secrets.WG_CONFIG_FILE }}
```
