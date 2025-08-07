# xRDP Linux Tuning

Comprehensive setup and optimization script for xRDP on Kubuntu/KDE Plasma systems.

## Features

- 🚀 **Performance Optimizations** - TCP buffer tuning, compression, and network optimizations
- 🖱️ **Cursor Fix** - Resolves the black cursor with white box issue common in xRDP
- 🖥️ **KDE/Plasma Integration** - Proper configuration for KDE desktop environment
- 🔓 **Network Authentication Fix** - Removes annoying NetworkManager password prompts
- 🎨 **Solid Background** - Option to set solid color backgrounds for better performance
- 🔐 **LAN Optimization** - Option to disable encryption for trusted networks
- 💾 **Persistent Sessions** - Reconnect to existing sessions after disconnect

## Quick Start

```bash
# Clone the repository
git clone git@github.com:jsbattig/xrdp-linux-tuning.git
cd xrdp-linux-tuning

# Make script executable
chmod +x xrdp-kubuntu.sh

# Apply all optimizations (recommended)
./xrdp-kubuntu.sh --all

# Or preview changes first
./xrdp-kubuntu.sh --dry-run --all
```

## Usage

```bash
./xrdp-kubuntu.sh [OPTIONS]
```

### Options

| Option | Description |
|--------|-------------|
| `--help` | Show help message |
| `--dry-run` | Preview changes without applying them |
| `--all` | Apply all configurations (recommended) |
| `--install` | Install xRDP and required packages |
| `--cursor-fix` | Fix black cursor with white box issue |
| `--performance` | Apply performance optimizations |
| `--kde-config` | Configure KDE/Plasma for xRDP |
| `--network-auth-fix` | Remove network manager authentication prompts |
| `--solid-bg [COLOR]` | Set solid background (default: #2b2b2b) |
| `--no-encryption` | Disable encryption for LAN (better performance) |
| `--persistent-sessions` | Enable persistent sessions |

### Examples

```bash
# Preview all changes
./xrdp-kubuntu.sh --dry-run --all

# Install and configure everything
./xrdp-kubuntu.sh --all

# Just fix the cursor issue
./xrdp-kubuntu.sh --cursor-fix

# Performance optimizations for LAN
./xrdp-kubuntu.sh --performance --no-encryption

# Set custom background color
./xrdp-kubuntu.sh --solid-bg "#404040"
```

## What It Does

### Performance Optimizations
- Increases TCP send/receive buffers to 512KB
- Enables bitmap caching and compression
- Optimizes network settings via sysctl
- Disables unnecessary xRDP channels
- Sets 24-bit color depth for balanced quality

### Cursor Fix
- Disables new_cursors in xrdp.ini
- Sets use_fastpath=none for Jump Desktop compatibility
- Configures DMZ-White cursor theme
- Sets XCURSOR_CORE=1 environment variable

### KDE/Plasma Configuration
- Creates optimized ~/.xsession file
- Disables KDE compositing for better performance
- Configures proper session startup
- Handles dbus session properly

### Network Authentication Fix
- Creates polkit rules to allow NetworkManager control
- Prevents authentication dialogs on login
- Allows color management without password

## Requirements

- Ubuntu/Kubuntu 22.04 or newer (tested on 24.04)
- KDE Plasma desktop environment
- sudo access for installation

## Tested With

- **OS**: Kubuntu 24.04 LTS
- **Desktop**: KDE Plasma 5/6
- **RDP Clients**: 
  - Jump Desktop (recommended)
  - Microsoft Remote Desktop (Windows/Mac)
  - mstsc.exe (Windows)

## Connection Information

After installation, connect using:
- **Port**: 3389
- **Username**: Your system username
- **Password**: Your system password

## Troubleshooting

### Black Screen After Login
- Make sure you're not logged in locally with the same user
- Try disconnecting and reconnecting
- Check that KDE session is properly configured

### Cursor Issues Persist
- Use mstsc.exe instead of newer Windows App
- Try Jump Desktop client for best compatibility

### Session Not Persisting
- Ensure `--persistent-sessions` option was applied
- Check that KillDisconnected=false in /etc/xrdp/sesman.ini

## Security Notes

⚠️ **Warning**: The `--no-encryption` option disables all encryption between client and server. Only use this on trusted local networks.

## Contributing

Feel free to open issues or submit pull requests with improvements.

## License

MIT License - See LICENSE file for details

## Author

Created with assistance from Claude Code

## Acknowledgments

- Based on extensive testing and optimization for Kubuntu/KDE environments
- Special optimizations for Jump Desktop client compatibility