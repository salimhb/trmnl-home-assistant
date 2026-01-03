# TRMNL HA

![TRMNL Logo](logo.png)

Send Home Assistant dashboard screenshots to your TRMNL e-ink display with advanced dithering optimized for e-paper screens.

[![Add repository to Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fusetrmnl%2Ftrmnl-home-assistant)

## Use Without Home Assistant

This add-on can capture screenshots from **any website**, not just Home Assistant dashboards.

```bash
# 1. Configure your target URL
cp ha-trmnl/options-dev.json.example ha-trmnl/options-dev.json
# Edit options-dev.json: set "home_assistant_url" to your website

# 2. Build and run
./ha-trmnl/scripts/docker-dev.sh

# 3. Capture screenshots
curl "http://localhost:10000/dashboard?viewport=800x480&dithering"
```

See [Standalone Mode](DOCS.md#standalone-mode) for detailed setup.

## Features

- **E-ink optimized dithering** - Floyd-Steinberg and Ordered algorithms for crisp e-paper rendering
- **TRMNL webhook integration** - Automatic dashboard uploads to TRMNL devices
- **Scheduled captures** - Cron-based automation with Web UI management
- **Device presets** - Pre-configured settings for 24+ popular e-ink displays
- **Crash recovery** - Automatic browser recovery and process supervision
- **High performance** - Powered by Bun runtime for fast startup and low memory

## Installation

1. Add this repository to Home Assistant:
   - Go to **Settings** → **Add-ons** → **Add-on Store** → **⋮** → **Repositories**
   - Add: `https://github.com/usetrmnl/trmnl-home-assistant`

2. Install the **TRMNL HA** add-on

3. Configure your access token:
   - In Home Assistant: **Profile** → **Long-Lived Access Tokens** → **Create Token**
   - Add to the add-on configuration

4. Start the add-on and open the Web UI

### Proxmox Users

If running Home Assistant OS in Proxmox, set the VM host type to `host` for Chromium to work properly.

## Security

**Important:** This add-on is designed for trusted home networks.

- The Web UI (port 10000) has **no built-in authentication**
- **Always use Ingress** (sidebar integration) instead of direct port access
- **Never expose port 10000** directly to the internet
- Access tokens are stored securely in Home Assistant's add-on configuration

## Documentation

| Topic | Description |
|-------|-------------|
| [Configuration](DOCS.md#configuration) | Required and optional settings |
| [Web UI](DOCS.md#web-ui) | Using the web interface |
| [API Reference](DOCS.md#api-reference) | Screenshot endpoint parameters |
| [Device Presets](DOCS.md#device-presets) | Supported e-ink displays |
| [Scheduled Captures](DOCS.md#scheduled-captures) | Cron-based automation |
| [Troubleshooting](DOCS.md#troubleshooting) | Common issues and fixes |
| [Local Development](DOCS.md#local-development) | Development setup |

## Attribution

This project is based on the [puppet](https://github.com/balloob/home-assistant-addons/tree/main/puppet) Home Assistant add-on by [Paulus Schoutsen](https://github.com/balloob).

See the [NOTICE](NOTICE) file for complete attribution and modification details.

## License

Copyright (c) Paulus Schoutsen (original work)
Copyright (c) 2024-2025 TRMNL (enhancements and modifications)

Licensed under the [Apache License 2.0](LICENSE)

## Links

- [TRMNL](https://usetrmnl.com)
- [Documentation](DOCS.md)
- [Changelog](CHANGELOG.md)
- [Upstream Project (puppet)](https://github.com/balloob/home-assistant-addons)
