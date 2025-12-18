# Changelog

All notable changes to this HomeLab configuration will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Security
- **Network Binding**: All container ports now bind to local IP address (192.168.1.110) instead of all interfaces, improving security posture
- **Network Isolation**: Public-facing services (exposed via SWAG) now share a dedicated `proxy` network, while local-only services have network configurations removed for better isolation

### Changed
- **Immich**: Simplified database container configuration
- **Jellyfin**: Removed `DOCKER_MODS=linuxserver/mods:jellyfin-opencl-intel` as Intel GPU transcoding no longer requires this modification
- **Rutorrent**: Removed `geo-ipupdater` container service (no longer needed)

### Added
- **Jellyseerr**: Added healthcheck configuration to monitor service availability and ensure proper startup sequencing
- **Homepage**: Added Gotify widget integration for notifications
- **SWAG**: Added UDP port 443 support to enable QUIC/HTTP3 protocol (requires additional configuration - see [SWAG QUIC documentation](https://github.com/linuxserver/docker-swag#quic-support))
- **WireGuard**: 
  - Configured `host` network mode to avoid conflicts with split tunneling
  - Added `wg0.conf` example configuration demonstrating split tunnel setup
  - Documented client configuration requirements for `AllowedIPs` field

### Documentation
- Added CHANGELOG.md to track configuration changes over time

---

## References

- [QUIC/HTTP3 Overview](https://www.cloudflare.com/es-es/learning/performance/what-is-http3/)
- [SWAG QUIC Setup Guide](https://github.com/linuxserver/docker-swag#quic-support)