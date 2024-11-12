# Android ROM Build Signing Script 🔐

A comprehensive bash script to automate the process of generating and setting up signing keys for custom ROMs. This script streamlines the process of creating a properly signed custom ROM build by handling all the necessary key generation and setup steps.

## Features ✨

- Automated key generation for all required signing keys
- Interactive certificate information collection
- Proper vendor directory structure setup for LineageOS 21+
- Comprehensive error handling and validation
- Color-coded output for better readability
- Automatic verification of the setup
- Security-focused with proper cleanup and warnings

## Prerequisites 📋

- Linux-based operating system
- ROM Sources e.g LineageOS 21+ source code
- The following tools installed:
  - `openssl`
  - `keytool`
  - `git`

## Installation 📥

1. Clone this repository or download the script:
```bash
git clone https://github.com/justkelvin/signing-script.git
```

2. Make the script executable:
```bash
chmod +x setup_signing.sh
```

## Usage 🚀

1. Navigate to your ROM source directory:
```bash
cd path/to/lineage/source
```

2. Run the script:
```bash
./setup_signing.sh
```

3. Follow the interactive prompts to enter your certificate information:
   - Country Code (2 letters)
   - State/Province
   - City/Locality
   - Organization
   - Email

## What the Script Does 🛠️

1. **Verification of Requirements**
   - Checks for required tools and commands
   - Validates the environment

2. **Key Generation**
   - Creates all necessary keys:
     - releasekey
     - platform
     - shared
     - media
     - networkstack
     - testkey
     - bluetooth
     - sdk_sandbox
     - verifiedboot

3. **Directory Setup**
   - Creates proper vendor directory structure
   - Sets up required configuration files
   - Moves keys to the correct location

4. **Configuration**
   - Creates `keys.mk` with proper certificate paths
   - Generates `BUILD.bazel` for Lineage 21+ compatibility

5. **Verification**
   - Ensures all keys were generated correctly
   - Verifies configuration files
   - Validates directory structure

## Directory Structure 📁

After running the script, the following structure will be created:
```
vendor/lineage-priv/
└── keys/
    ├── releasekey.pk8
    ├── releasekey.x509.pem
    ├── platform.pk8
    ├── platform.x509.pem
    └── ... (other key pairs)
    ├── keys.mk
    └── BUILD.bazel
```

## Security Considerations 🔒

⚠️ **IMPORTANT:**
- Never share or publish your signing keys
- Keep secure backups of your keys
- Don't set passwords for the keys as it breaks the build process
- Treat builds signed with these keys as official signatures

## Troubleshooting 🔍

If you encounter issues:

1. Ensure you're in the LineageOS source directory
2. Check if all prerequisites are installed
3. Verify you have proper permissions
4. Look for detailed error messages in the output

Common issues:
- `make_key not found`: You're not in the ROMs source directory
- `Permission denied`: Run with proper user permissions
- `Missing requirements`: Install required tools

## Contributing 🤝

Contributions are welcome! Please feel free to submit a Pull Request.

## License 📄

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments 👏

- LineageOS Team for the original signing documentation
- Android Open Source Project for the base tools
- Community contributors and testers

## Support 💬

If you encounter any issues or have questions:
1. Check the troubleshooting section
2. Open an issue on GitHub
3. Join our discussion in the LineageOS community forums

---

**Note**: This script is not officially associated with LineageOS. Always verify signing procedures against official documentation.
