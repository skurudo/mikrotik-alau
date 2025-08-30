# ALAU - AddressList Auto Update

## Project Description

**ALAU** is a script for automatically updating address lists (AddressList) in MikroTik RouterOS from remote sources via HTTP/HTTPS.

## Features

- Automatic updating of address lists from remote sources
- HTTP/HTTPS protocol support
- Automatic cleanup of old entries before importing new ones
- Comprehensive logging of all operations
- Versatile usage for various purposes:
  - Block lists (blacklist)
  - Allow lists (whitelist)
  - Favorite IP address lists
  - Any other address lists

## Project Structure

- `alau.script` - main RouterOS script
- `test.rsc` - example address list file
- `README.md` - Russian documentation
- `README_EN.md` - English documentation

## How to Use

1. Upload the `alau.script` to your MikroTik router
2. Configure parameters in the script:
   - `addrlistname` - name of the address list
   - `addrlisturl` - URL for file download
   - `addrlistfilename` - filename to download
3. Run the script in RouterOS

## Address List File Format

The file must be in `.rsc` (RouterOS Script) format with the following structure:

```
/ip firewall address-list
add address=IP_ADDRESS comment=COMMENT list=LIST_NAME
```

## Requirements

- MikroTik RouterOS
- Internet access for file downloads
- Properly formatted .rsc file

## Versions

### v01
- Basic functionality
- Dynamic addresses may not work correctly
- .rsc file format is critical
- Address list in .rsc file is stable but requires format verification

## How It Works

The script performs the following operations:
1. Downloads the address list file from the specified URL
2. Checks if the file was downloaded successfully
3. Clears the existing address list
4. Imports the new address list from the downloaded file
5. Removes the temporary file
6. Logs all operations for monitoring

## Use Cases

- **Security**: Automatically update blacklists from security services
- **Access Control**: Maintain whitelists for allowed IP addresses
- **Network Management**: Keep lists of favorite or important IP addresses
- **Automation**: Eliminate manual updates of address lists

## Configuration Example

```bash
# In alau.script
:local addrlistname "blocked_ips"
:local addrlisturl "https://example.com/lists"
:local addrlistfilename "blocked.rsc"
```

## Troubleshooting

- Ensure the .rsc file format is correct
- Check internet connectivity
- Verify the URL is accessible
- Monitor logs for error messages

## Author

Project created for automating address list management in MikroTik RouterOS.
