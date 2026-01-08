# dualonyxpi

Setup scripts for Soracom Starter Kit devices.

## EG25 dual modem setup

The `setup_eg25.sh` script configures NetworkManager and ModemManager for EG25-G modems,
including dual-modem setups. It creates per-device `soracom-<device>` connection profiles
(e.g., `soracom-cdc-wdm0`, `soracom-cdc-wdm1`) and applies Soracom routing rules.

### Usage

Run the script as root (default APN `soracom.io`):

```bash
sudo ./setup_eg25.sh
```

To provide a custom APN/credentials:

```bash
sudo ./setup_eg25.sh <apn> <username> <password>
```

After running the script, list Soracom profiles and manually reconnect as needed:

```bash
nmcli con show | grep soracom
sudo nmcli con down soracom-<device>
sudo nmcli con up soracom-<device>
```
