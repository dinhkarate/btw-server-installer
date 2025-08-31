# BTW Server Installer

**Purpose**  
This repository is **only for linux server installation** of the Better Than Wolves mod.  
It is designed for Linux distributions that use the `apt` package manager (e.g., Debian, Ubuntu, and derivatives).

**Not for client installation**  
If you are looking for client installation instructions, please see:  
- [Wiki BTWCE](https://wiki.btwce.com/index.php?title=3.0.0_Beta)  
- [BTW Installer](https://github.com/GencoreOperative/btw-installer)

---

## How to use (Server installation)

Copy and paste into your terminal:

```bash
sudo apt update
sudo apt install openjdk-17-jre -y

sudo ufw allow 25565/tcp
sudo ufw allow 25565/udp
sudo ufw reload

curl -o legacy.jar "https://repo.legacyfabric.net/legacyfabric/net/legacyfabric/fabric-installer/1.1.0/fabric-installer-1.1.0.jar"
java -jar legacy.jar server -mcversion 1.6.4 -loader 0.15.11 -downloadMinecraft

mkdir -p mods
curl -L -o mods/btw-fabric-3.0.0-beta-snapshot-5.jar "https://github.com/dinhkarate/btw-server-installer/releases/download/v3.0.0-beta-snapshot.5/btw-fabric-3.0.0-beta-snapshot-5.jar"

cat > start.sh <<'EOF'
#!/bin/bash
java -Xmx2G -Xms1G -jar fabric-server-launch.jar nogui
EOF

chmod +x start.sh
echo "✅ Setup completed. Run server with: ./start.sh"
```

You can change `-Xmx2G -Xms1G` in `start.sh` to fit your hardware configuration.

---

## Optional Mods

Place additional `.jar` files in the `mods/` folder. Some community mods can be installed with CLI commands.  
For example, **[Dynamic Lights](https://github.com/BTW-Community/Dynamic-Lights-3):**

```bash
curl -L -o mods/dynamiclights-1.2.0.jar "https://github.com/BTW-Community/Dynamic-Lights-3/releases/download/3.0/dynamiclights-1.2.0.jar"
```

---

## Disclaimer

I am **not the author or owner** of the Better Than Wolves mod.  
All rights belong to the original creator(s).  
The mod files are only mirrored here on GitHub for **convenience of download and installation**.  

If you enjoy the mod, please support the original developer here:  
👉 [Official Better Than Wolves Discord](https://discord.com/invite/fhMK5kx)
