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
