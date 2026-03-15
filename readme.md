<div align="center">

<img src="images/robbenlogo-glinet-small.webp" width="300" alt="GL.iNet Tailscale Logo" style="border-radius: 10px; margin: 20px 0;">

## Tailscale Updater for GL.iNet Routers

**Keep Tailscale up-to-date on your GL.iNet router with ease!**

[![Latest Release](https://img.shields.io/badge/release-v1.94.2-blue?style=for-the-badge&logo=github)](https://github.com/Admonstrator/glinet-tailscale-updater/releases/latest) [![License](https://img.shields.io/github/license/Admonstrator/glinet-tailscale-updater?style=for-the-badge)](LICENSE) [![Stars](https://img.shields.io/badge/stars-538-brightgreen?style=for-the-badge&logo=github)](https://github.com/Admonstrator/glinet-tailscale-updater/stargazers)

---

## 💖 Support the Project

If you find this tool helpful, consider supporting its development:

[![GitHub Sponsors](https://img.shields.io/badge/GitHub-Sponsors-EA4AAA?style=for-the-badge&logo=github)](https://github.com/sponsors/admonstrator) [![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/admon) [![Ko-fi](https://img.shields.io/badge/Ko--fi-FF5E5B?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/admon) [![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/aaronviehl)

</div>

---

## 📖 About

This script automatically fetches and installs the latest Tailscale version, optimized specifically for GL.iNet routers. Keep your Tailscale installation current with just one command!

Created by [Admon](https://forum.gl-inet.com/u/admon/) for the GL.iNet community. Tested on nearly all GL.iNet routers with firmware 4.x.

> 🎖️ **Community Maintained** – Part of the [GL.iNet Toolbox](https://github.com/Admonstrator/glinet-toolbox) project  
> ⚠️ **Independent Project** – Not officially affiliated with GL.iNet or Tailscale

---

## ✨ Features

- 🚀 **Automatic Updates** – Fetches and installs the latest Tailscale version
- 📦 **Tiny Version Support** – Uses optimized tiny binaries to save space
- 🗜️ **UPX Compression** – Further reduces binary size when needed
- 🔒 **Tailscale SSH Ready** – Enables secure SSH access to the router via Tailscale
- 🎯 **Version Selection** – Install specific Tailscale versions
- 🔧 **Stateful Filtering** – Auto-configures for exit node compatibility
- 🛡️ **Safe Restore** – Restore original firmware binaries if needed
- ⚡ **Flexible Options** – Multiple flags for customized installations

---

## 📋 Requirements

| Requirement | Details |
|-------------|---------|
| **Router** | GL.iNet router with firmware 4.x (including GL-BE9300 Flint 3) |
| **Architecture** | arm64, armv7, mips, mipsle, or x86_64 |
| **Free Space** | At least 15 MB (can be bypassed with `--ignore-free-space`) |

> ⚠️ **Please make sure, that you enabled Tailscale in the GL.iNet router settings before running this script!**

---

## 🚀 Quick Start

Run the updater without cloning the repository:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh
```

> ⚠️ **Important:** Do not run this script as a cron job! Manual execution is recommended.

---

## 🎛️ Arguments

The `update-tailscale.sh` script supports the following arguments:

| Argument | Description |
|----------|-------------|
| `--ignore-free-space` | Bypasses the free space check. Use with caution on low-storage devices! |
| `--force` | Skips all confirmation prompts and makes installation permanent. Ideal for unattended installations. |
| `--force-upgrade` | Forces upgrade even if the current version is already up to date. Useful for reinstalling the same version. |
| `--restore` | Restores original firmware binaries (`/usr/sbin/tailscaled` and `/usr/sbin/tailscale`). ⚠️ Does not restore config files! |
| `--no-upx` | Skips UPX compression. Binaries will be larger but installation is faster. |
| `--no-download` | Skips downloading binaries. Use pre-downloaded archive at `/tmp/tailscale.tar.gz`. |
| `--no-tiny` | Uses full Tailscale binaries instead of tiny version. Not recommended for GL.iNet routers. |
| `--skip-config` | Skips the adjustment of the gl_tailscale script. |
| `--select-release` | Displays available releases and lets you choose a specific version. ⚠️ Downgrading not officially supported! |
| `--testing` | Uses prerelease/testing versions from the testing branch. ⚠️ Use at your own risk! May contain bugs or experimental features. |
| `--ssh` | Enables Tailscale SSH feature after installation. |
| `--log` | Shows timestamps in all log messages. Useful for debugging and tracking execution time. |
| `--ascii` | Uses ASCII characters (`[OK]`, `[X]`, `[!]`, `[->]`) instead of emojis for compatibility with older terminals. |
| `--help` | Displays help message with all available arguments. |

---

## 📚 Usage Examples

### Standard Update

Update to the latest stable release:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh
```

### Testing/Prerelease Versions

Install prerelease versions from the testing branch for early access to new features:

```bash
sh update-tailscale.sh --testing
```

> ⚠️ **Warning:** Testing versions are experimental and may contain bugs or unstable features. Use at your own risk!

### Select a Specific Version

Install a specific Tailscale version (useful if the latest version has issues):

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --select-release
```

The script will display available releases for you to choose from.

> ⚠️ **Warning:** Downgrading Tailscale is not officially supported and may cause unexpected behavior.

### Force Update (Unattended Installation)

Skip all prompts and make the installation permanent:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --force
```

Combine with `--ignore-free-space` for devices with limited storage:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --force --ignore-free-space
```

### Restore Original Binaries

Revert to the original firmware binaries:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --restore
```

> ⚠️ **Caution:** This does not restore configuration files and may result in a broken installation.

### Logging and Output Options

Enable timestamps for debugging or tracking execution time:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --log
```

Use ASCII characters instead of emojis for compatibility with older terminals:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --ascii
```

Combine both options:

```bash
wget -q https://get.admon.me/tailscale -O update-tailscale.sh ; sh update-tailscale.sh --log --ascii
```

---

## 🔍 Key Features Explained

### 🎯 Tailscale Stateful Filtering

The script automatically adds `--stateful-filtering=false` to the `gl_tailscale` script. This is required for proper exit node functionality on GL.iNet routers.

The modification is:
- ✅ Applied automatically
- ✅ Permanent (survives firmware upgrades)
- ✅ No manual configuration needed

### 🔐 Tailscale SSH Ready

If you agree to enable Tailscale SSH during installation (manually or by using `--ssh`), the script will automatically configure Tailscale SSH after updating. You can read more about Tailscale SSH [here](https://tailscale.com/kb/1193/tailscale-ssh).

> ⚠️ **Warning:** If you are connected to your router via Tailscale SSH, you will be disconnected when SSH support is enabled. This might cause the script to terminate prematurely. It is recommended to run the script via local SSH or via GoodCloud SSH terminal.

### 📦 Tiny-Tailscale

By default, the script uses optimized tiny binaries that:
- 🔹 Significantly reduce storage footprint
- 🔹 Maintain useful functionality for routers
- 🔹 Skip UPX compression (already optimized)
- 🔹 Are recommended for all GL.iNet routers

Use `--no-tiny` if you need the full-sized binaries.

### 🗜️ UPX Compression

For standard (non-tiny) binaries, UPX compression:
- 🔹 Substantially reduces binary size
- 🔹 Is recommended for storage-limited devices
- 🔹 Requires `xz` (auto-installed if missing)
- 🔹 Can be disabled with `--no-upx`

---

## 📸 Screencast

<div align="center">

<img src="images/screencast.gif" width="600" alt="Tailscale Updater Screencast" style="border-radius: 10px; margin: 20px 0;">

</div>

---

## 💡 Getting Help

Need assistance or have questions?

- 💬 [Join the discussion on GL.iNet Forum](https://forum.gl-inet.com/t/how-to-update-tailscale-on-arm64/37582) – Community support
- 💬 [Join GL.iNet Discord](https://link.gl-inet.com/website-discord-support) – Real-time chat
- 🐛 [Report issues on GitHub](https://github.com/Admonstrator/glinet-tailscale-updater/issues) – Bug reports and feature requests
- 📧 Contact via forum private message – For private inquiries

---

## ⚠️ Disclaimer

This script is provided **as-is** without any warranty. Use it at your own risk.

It may potentially:
- 🔥 Break your router, computer, or network
- 🔥 Cause unexpected system behavior
- 🔥 Even burn down your house (okay, probably not, but you get the idea)

**You have been warned!**

Always read the documentation carefully and understand what a script does before running it.

---

## 👥 Contributors

Special thanks to:

- [lwbt](https://github.com/lwbt) – UPX compression & tiny-tailscale feature
- [Aubermean](https://github.com/Aubermean) – Clarification of `--stateful-filtering=false` ([#1](https://github.com/Admonstrator/glinet-tailscale-updater/issues/1))
- All the testers and feedback providers in the GL.iNet forum!
- Copilot – Yeah, I am using AI to help write code. But I review and test everything thoroughly!

Want to contribute? Pull requests are welcome!

---

## 📜 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

<div align="center">

## 🧰 Part of the GL.iNet Toolbox

This project is part of a comprehensive collection of tools for GL.iNet routers.

**Explore more tools and utilities:**

[![GL.iNet Toolbox](https://img.shields.io/badge/🧰_GL.iNet_Toolbox-Explore_All_Tools-blue?style=for-the-badge)](https://github.com/Admonstrator/glinet-toolbox)

*Discover AdGuard Home Updater, ACME Certificate Manager, and more community-driven projects!*

</div>

---

<div align="center">

**Made with ❤️ by [Admon](https://github.com/Admonstrator) for the GL.iNet Community**

⭐ If you find this useful, please star the repository!

</div>

<div align="center">

_Last updated: 2026-03-15_

</div>
