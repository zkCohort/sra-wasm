# Changelog

All notable changes to this project will be documented in this file.

## [v0.1.0] - 2023-11-04

### Changed

- Fix outdated implementation for generating keypair in README.md
- Change constraint on upper limit of key size from `u128::MAX / 2` to `phi.bits()` in generate_key_pair
- Tests for large `bit_size` values `256`, `512`, `1024` and `2048` added.  The `bit_size` parameter affects the size of `phi` and `N`, subsequently affecting the size of the keypair which will be roughly half of `phi.bits()`.

## [v0.0.3] - 2023-11-04

### Added

- Badges to README
- GitHub Actions

### Changed

- Clippy cleanup (Passing n no longer required to generate keypair)

## [v0.0.2] - 2023-11-04

### Changed

- Documentation updated

## [v0.0.1] - 2023-11-03

### Added

- Initial release
