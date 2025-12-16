
## 1️⃣ Identify your network interface

First, find the interface name (e.g. `eth0`, `ens18`, `enp0s3`):

```bash
ip a
```

Example interface name:

```
ens18
```

---

## 2️⃣ Edit the Netplan configuration

Netplan configs are in `/etc/netplan/`

List files:

```bash
ls /etc/netplan/
```

Usually you’ll see something like:

* `00-installer-config.yaml`
* `01-netcfg.yaml`

Edit the file:

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

---

## 3️⃣ Example Static IP configuration (IPv4)

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: no
      addresses:
        - 192.168.1.50/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 1.1.1.1
```

### Replace with your values:

* **ens18** → your interface name
* **192.168.1.50** → desired static IP
* **/24** → subnet mask (255.255.255.0)
* **192.168.1.1** → router/gateway
* DNS → your preferred DNS servers

⚠️ **YAML is indentation-sensitive** (use spaces, not tabs).

---

## 4️⃣ Apply the configuration

Before applying, test it safely:

```bash
sudo netplan try
```

If everything works, it will auto-apply.
Or apply directly:

```bash
sudo netplan apply
```

---

## 5️⃣ Verify the static IP

```bash
ip a
ip route
```

Test connectivity:

```bash
ping -c 4 8.8.8.8
ping -c 4 google.com
```

---
