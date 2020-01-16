# Tarkov
An unofficial client library for the [Escape from Tarkov](https://escapefromtarkov.com) (EFT) API.

This library is currently in alpha. Everything may change significantly in future releases.

## Features
- [x] Authentication
- [x] Flea market
- [x] Friends
- [ ] Hideout
- [ ] Inventory management (examine, move, delete, etc)
- [ ] Quests
- [x] Traders
- [ ] Messenger

## Getting Started

Comprehensive examples can be found in the [`examples`](examples) directory.

### Usage
Add this to your `Cargo.toml`:
```
[dependencies]
tarkov = "0.1"
```

### Authentication
![Authentication flowchart](flow.png)
There are three ways to authenticate your EFT account for `tarkov`:
1. Email & password is the easiest way to authenticate your account. However, a captcha and 2FA code may be required. Read the [HWID section](#hardware-id) for more details.
2. Access token or Bearer token can be found by sniffing EFT _launcher_ traffic. Captcha and 2FA code may be required.
3. Session is a cookie called `PHPSESSID`, it can be found by sniffing EFT _game_ traffic. HWID is not required for this method.

**Your _PMC_ character profile must be selected with `select_profile` to complete the authentication.**

### Hardware ID
Hardware ID (HWID) may be required on authentication, it can either be sniffed from the EFT _launcher_ or [generated](https://docs.rs/todo). It's recommended to save the HWID in a _persistent store_ and reuse it after the first successful authentication.

Using a fresh HWID means both captcha and 2FA code will be required on your first login attempt. This can be avoid by using the HWID generated by the EFT launcher.

### Rust Version
`tarkov` has a minimum version requirement of `1.39.0` as it uses the `async_await` feature.

## "Unofficial"

I should emphasize that this library is _unofficial_. EFT does not have a public API, everything in this repo was reversed from the game.

The API is clearly designed for internal use. It contains numerous spelling mistakes, inconsistent conventions, and tons of bad practice JSON. The developers may push breaking changes without prior warning.

## License
[MIT](LICENSE)
