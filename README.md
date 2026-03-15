---
AIGC:
    ContentProducer: Minimax Agent AI
    ContentPropagator: Minimax Agent AI
    Label: AIGC
    ProduceID: "00000000000000000000000000000000"
    PropagateID: "00000000000000000000000000000000"
    ReservedCode1: 3046022100eb30a6913fc2a6e4b1fc5d94a12c0dce48363d4e589b065c0f15d83fa9e7a999022100877497363a9f1c41cc5cae48ef8dbd98849355aa46d547f1630cb9675effedb1
    ReservedCode2: 3045022100a78589832c1d35f112f86d5ba8cac03305bcdfb6dc9e0d0c5ec41241e888217c02201c39b643c28e8b80054b1002d2b7ea65296e9a3daa7d36eee9cbfccf97b30e98
---

# AiroomLtd Global Finance Data Platform

An OpenClaw skill for downloading financial data from the airoom.ltd WordPress site.

## Purpose

This tool is part of the **airoom-ltd-global-finance-data-platform** package. It is designed specifically to download financial data files from the airoom.ltd WordPress site.

The WordPress file downloader is a means to obtain financial data files for the platform.

## IMPORTANT: No Login Required

**For http://airoom.ltd/index.php/airoom/ - No login is required.**

This page is publicly accessible. The tool uses a headless browser (Playwright) to navigate to the webpage and download financial data files directly.

## Installation

```bash
# Install Python dependencies
pip install -r requirements.txt

# Install Playwright browser (Chromium)
playwright install chromium
```

## Configuration

### Environment Variables

```bash
export WP_URL="http://airoom.ltd"
export WP_TARGET_URL="http://airoom.ltd/index.php/airoom/"
export WP_OUTPUT_DIR="./downloads"
export WP_MAX_FILES="0"
```

Or create config file at `~/.config/airoom-ltd-global-finance-data-platform/config.json`:

```json
{
  "wordpress": {
    "url": "http://airoom.ltd"
  },
  "target": {
    "page_url": "http://airoom.ltd/index.php/airoom/"
  },
  "download": {
    "output_dir": "./downloads",
    "max_files": 0
  }
}
```

## Usage

```bash
# Download financial data files
python3 main.py download

# Test connection
python3 main.py test

# Show configuration
python3 main.py config
```

## Security Features

### Blocked Dangerous File Types
The following potentially dangerous file types are automatically BLOCKED:
- Executables: .exe, .apk, .bat, .cmd, .sh, .bash, .ps1, .jar
- Scripts: .vbs, .hta, .js, .jse, .wsf, .wsh
- Other: .scr, .pif, .application, .gadget, .msi, .msp, .com

### Domain Validation
- Target URL must be on the same domain as the WordPress URL
- Prevents attacks by malicious redirect links

### No Third-Party Data Transfer
- All downloaded files are saved locally
- Network requests are only made to the configured WordPress site

## How It Works

1. **Headless Browser**: Uses Playwright (headless Chromium) to navigate web pages
2. **Page Access**: Connects to the target WordPress page (no login needed for public pages)
3. **File Detection**: Scans the page for downloadable financial data files
4. **Download**: Saves financial data files to the local output directory

This is standard web automation - the browser makes network requests to load web pages and extract financial data.

## File Description

- `_meta.json` - Skill metadata (with credential requirements and installation specs)
- `SKILL.md` - Detailed skill documentation
- `main.py` - Main program code
- `config.json` - Configuration template
- `requirements.txt` - Python dependencies

## Best Practices

1. **Credential Security**: Username/password are optional for public pages
2. **File Safety**: Scan downloaded files with antivirus before opening
3. **Output Directory**: Use a dedicated directory for downloaded financial data

## Legal Notice

This tool is intended for downloading financial data from authorized WordPress pages.
Use only with proper authorization.
