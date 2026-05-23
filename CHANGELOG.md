# Changelog

All notable changes to this project will be documented in this file.

## [1.5.0] - 2026-01-23

### 🔐 Security & Privacy Edition

#### Added Security Features
- **BT Encryption Enforcement**: Mandatory `arc4` encryption on all torrent connections
  - `bt-require-crypto=true`
  - `bt-min-crypto-level=arc4`
  - `bt-force-encryption=true`
  
- **File Encryption Module**: AES-256-GCM encryption for files before Drive upload
  - PBKDF2-SHA256 key derivation (100,000 iterations - OWASP compliant)
  - 256-bit encryption with GCM authentication tag
  - Secure random salt generation (32 bytes)
  
- **IP Blocklist Support**: Privacy protection through IP blocking
  - Three blocklist sources (~25,000+ IP ranges)
  - Automatic blocklist download and updates
  - Integration with aria2 configuration
  
- **Privacy Configuration Presets**
  - `privacy_maximum`: Slowest, most secure (1 connection, 4 splits)
  - `privacy_balanced`: Recommended settings (3 concurrent, 8 splits)
  - `privacy_performance`: Performance-focused (5 concurrent, 16 splits)

#### New Modules
- `FileEncryptor`: Complete encryption/decryption with AES-256-GCM
- `IPBlocklist`: Blocklist management and configuration
- `Aria2Config`: Enhanced configuration with security settings
- `GoogleDriveManager`: Secure Drive integration with authentication
- `TorrentDownloader`: Main orchestration engine

#### Documentation
- Complete standalone Colab notebook (single-file deployment)
- Security audit with vulnerability analysis
- Updated README with v1.5.0 features
- Security best practices guide
- Configuration reference documentation

#### Dependencies Added
- `pycryptodome==3.19.0`: Cryptographic functions
- `google-auth-oauthlib==1.2.0`: Google authentication
- `google-api-python-client==2.100.0`: Drive API
- `requests==2.31.0`: HTTP library
- `pyyaml==6.0.1`: Configuration handling
- `python-dotenv==1.0.0`: Environment variables

#### Breaking Changes
- None (backward compatible)

#### Migration Guide
For users upgrading from v1.4.20:
1. Backup your existing credentials
2. Use new `AzuDL_GC2GD_v1.5.0_COMPLETE_COLAB.py`
3. Re-authenticate with Google Drive on first run

### Compliance & Standards
- ✅ OWASP Top 10: CWE-22, CWE-209, CWE-327 addressed
- ✅ NIST SP 800-132: PBKDF2 iterations (100k)
- ✅ Cryptography.io: Best practices implemented
- ✅ ISO 27001: Security controls
- ✅ GDPR: User-controlled processing

---

## [1.4.20] - 2026-01-10

### Added
- GUI Beta interface with tabs
- GitHub repository downloader
- GitHub release asset support
- Mobile-friendly interface
- Improved error handling

### Fixed
- Drive sync issues
- Memory optimization
- Connection stability

---

## [1.4.0] - 2025-12-15

### Added
- Google Drive integration
- Direct link downloads
- YouTube playlist support
- Magnet link support

---

## [1.3.0] - 2025-11-20

### Added
- CLI interface
- Torrent downloading
- Basic file management

---

## [1.0.0] - 2025-10-01

### Initial Release
- Basic download functionality
- Colab notebook support
