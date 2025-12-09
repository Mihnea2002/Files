# Windows DNS Change - Quick Guide

## Method 1: GUI (Easiest)

1. Press `Win + R` → Type `ncpa.cpl` → Press Enter
2. Right-click your active network connection → Properties
3. Select "Internet Protocol Version 4 (TCP/IPv4)" → Properties
4. Select "Use the following DNS server addresses"
5. Enter:
   - Preferred DNS: `1.1.1.1` (Cloudflare)
   - Alternate DNS: `8.8.8.8` (Google)
6. Click OK → Close all
7. Open Command Prompt (Win+R → cmd)
8. Run: `ipconfig /flushdns`
9. Restart browser and try Claude.ai

## Method 2: Command Line (Faster)

Open PowerShell as Administrator (Win+X → Windows PowerShell (Admin)):

```powershell
# Find your network adapter name
Get-NetAdapter

# Set DNS (replace "Ethernet" with your adapter name from above)
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses ("1.1.1.1","8.8.8.8")

# Or if WiFi:
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddresses ("1.1.1.1","8.8.8.8")

# Flush DNS cache
ipconfig /flushdns

# Verify
nslookup claude.ai
```

## Method 3: Browser-Level DNS (If system DNS fails)

### Firefox:
1. Settings → Privacy & Security
2. Scroll to "DNS over HTTPS" → Enable
3. Select "Cloudflare" or "Custom" → Use `https://1.1.1.1/dns-query`

### Chrome/Edge:
1. Settings → Privacy and security → Security
2. Scroll to "Use secure DNS"
3. Select "Cloudflare (1.1.1.1)"

After changing DNS, restart browser and test Claude.ai
