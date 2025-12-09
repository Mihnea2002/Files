# How to Change DNS to Bypass Blocking

## Windows:
1. Open Control Panel → Network and Sharing Center
2. Click your connection → Properties
3. Select "Internet Protocol Version 4 (TCP/IPv4)" → Properties
4. Select "Use the following DNS server addresses"
5. Enter:
   - Preferred: `8.8.8.8`
   - Alternate: `1.1.1.1`
6. Click OK and restart browser

## Linux:
```bash
# Edit resolv.conf
sudo nano /etc/resolv.conf

# Add these lines:
nameserver 8.8.8.8
nameserver 1.1.1.1

# Save and exit (Ctrl+X, Y, Enter)

# Test
nslookup claude.ai
```

## macOS:
1. System Preferences → Network
2. Select your connection → Advanced
3. DNS tab → Click "+"
4. Add: `8.8.8.8` and `1.1.1.1`
5. Click OK → Apply

## Browser-level DNS (Firefox):
1. Settings → Privacy & Security
2. Scroll to "DNS over HTTPS"
3. Enable it and select "Cloudflare"
4. This bypasses system DNS

## Test if it worked:
Visit: https://claude.ai
Try sending a message
