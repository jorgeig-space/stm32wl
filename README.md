# Differences with upstream crate

The crates generated with `svd2rust` from `stm32-rs` now depend on `cortex-m-rt` `>0.6.15,<0.8`. This causes cargo to choose 0.7.0 at the moment. Unforunately cortex-m-rt 0.7.0

# stm32wl
This crate provides an autogenerated API for access to STM32WL peripherals.
The API is generated using [svd2rust] with patched svd files containing
extensive type-safe support. For more information please see the [main repo].

Refer to the [documentation] for full details.

[svd2rust]: https://github.com/japaric/svd2rust
[main repo]: https://github.com/stm32-rs/stm32-rs
[documentation]: https://docs.rs/stm32wl/latest/stm32wl/

## Usage
Each device supported by this crate is behind a feature gate so that you only
compile the device(s) you want. To use, in your Cargo.toml:

```toml
[dependencies.stm32wl]
version = "0.13.0"
features = ["stm32wl5x_cm0p", "rt"]
```

The `rt` feature is optional and brings in support for `cortex-m-rt`.

In your code:

```rust
use stm32wl::stm32wl5x_cm0p;

let mut peripherals = stm32wl5x_cm0p::Peripherals::take().unwrap();
let gpioa = &peripherals.GPIOA;
gpioa.odr.modify(|_, w| w.odr0().set_bit());
```

For full details on the autogenerated API, please see:
https://docs.rs/svd2rust/0.19.0/svd2rust/#peripheral-api

## Supported Devices

| Module | Devices | Links |
|:------:|:-------:|:-----:|
| stm32wl5x_cm0p | STM32WL5X (CM0+) | [RM0453](https://www.st.com/resource/en/reference_manual/dm00451556-stm32wl5x-advanced-armbased-32bit-mcus-with-subghz-radio-solution-stmicroelectronics.pdf), [st.com](https://www.st.com/en/microcontrollers-microprocessors/stm32wl5x.html) |
| stm32wl5x_cm4 | STM32WL5X (CM4) | [RM0453](https://www.st.com/resource/en/reference_manual/dm00451556-stm32wl5x-advanced-armbased-32bit-mcus-with-subghz-radio-solution-stmicroelectronics.pdf), [st.com](https://www.st.com/en/microcontrollers-microprocessors/stm32wl5x.html) |
| stm32wle5 | STM32WLE5 | [RM0461](https://www.st.com/resource/en/reference_manual/dm00530369-stm32wlex-advanced-armbased-32bit-mcus-with-subghz-radio-solution-stmicroelectronics.pdf), [st.com](https://www.st.com/en/microcontrollers-microprocessors/stm32wlex.html) |
