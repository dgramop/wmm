# wmm2
[![ci](https://github.com/dgramop/wmm/workflows/ci/badge.svg)](https://github.com/dgramop/wmm/actions?query=workflow%3Aci)
[![license](https://img.shields.io/badge/license-MIT%20or%20Apache--2-brightgreen)](https://github.com/sevenseas-io/wmm#license)
[![version](https://img.shields.io/crates/v/wmm.svg)](https://crates.io/crates/wmm)
[![minimum rustc: 1.59](https://img.shields.io/badge/minimum%20rustc-1.59-yellowgreen?logo=rust)](https://www.whatrustisit.com)
[![docs](https://docs.rs/wmm2/badge.svg)](https://docs.rs/wmm2/)

Low footprint `no_std` World Magnetic Model (WMM) library used to calculate the magnetic declination at sea level.

It's important to note that the current model is valid from 2020 until 2025.

To give an easy upgrade path to project using sevenseas.io's defunct/disappeared `wmm`, this repository (soon to be published as `wmm2`) is a hard-fork of the defunct `wmm`, and will incude the new coefficints once released, and will incude the new coefficints once released (December 17th, 2024)

The original respository is missing, the people behind it are unreachable, the whois lookup for the domain for the company is withheld for privacy. So, credit for the original development belongs to someone other than me, though I take custodianship of this code since I need it to work.

## Example

```rust
use time::OffsetDateTime;
use wmm::declination;

fn main() {
    let date = OffsetDateTime::now_utc().date();
    let lat = 29.7363025;
    let lon = -93.8827939;
    let dec = declination(date, lat, lon).unwrap();

    println!(
        "Today's declination for coordinates {},{} is {}°",
        lat, lon, dec
    )
}
```

## Minimum Supported Rust Version (MSRV)

This crate is guaranteed to compile on stable Rust 1.59 and up.

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

## Credits

The C code this library refences originates from [WMM_Tiny](https://github.com/miniwinwm/WMM_Tiny).

The [WMM](https://www.ngdc.noaa.gov/geomag/WMM/) is a NOAA effort which is part of the US Government.
