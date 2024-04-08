# dht20
Rust driver for dht20 temp/hum sensor.
Works on all platforms that implement embedded_hal.

## Usage
```rust
let mut sensor = Dht20::new(
    i2c/*platform specific i2c driver*/,
    0x38,
    esp_idf_hal::delay::Delay/*platform specific delay*/,
);
match sensor.read() {
    Ok(reading) => println!("Temp: {} °C, Hum: {} %",reading.temp, reading.hum),
    Err(e) => {
        error!("Error reading sensor: {e:?}");
    }
}
```

## Embedded-Hal 1.0 Support

To use embedded-hal 1.0 traits bounds instead of the default embedded hal 0.2.7 bounds edit Cargo.toml to disable default features and use the "embedded-hal-1" feature.  If dht20 is already included in the project, the embedded-hal 1.0 trait bounds can be used by editing Cargo.toml as follows:

```toml
[dependencies.dht20]
version = "x.x.x"
default-features = false
features = ["embedded-hal-1"]
```

To add dht20 as a dependency using the embedded-hal 1.0 trait bounds run:

```bash
cargo add --no-default-features --features embedded-hal-1 dht20
```
