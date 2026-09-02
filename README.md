# DHT11 Humidity and Temperature Sketch

A minimal Arduino sketch that reads temperature and humidity from a DHT11 sensor and
prints both over serial. I wrote this early on while learning Arduino. It's about as
small as a working sensor sketch gets, and it's mostly useful for confirming a DHT11 is
wired up correctly before building anything on top of it.

## Setup

The sketch depends on the `dht11` library, which is bundled here as `Dht11.zip`. In the
Arduino IDE, go to **Sketch → Include Library → Add .ZIP Library** and pick that file.

Wire the sensor's data line to **digital pin 8**, or change `DHT11PIN` in `DHT11.ino` if
you've wired it elsewhere.

## Usage

Upload `DHT11.ino` and open the Serial Monitor at **9600 baud**. It prints a tab-separated
reading every 500 ms, with temperature in degrees Celsius:

```
Temperature=23 C	Humidity=%45
```

## Limitations

`DHT11.read()` returns a status code and the sketch ignores it, so a wiring fault or a
failed checksum shows up as a stale or zero reading rather than an error. There's no
averaging either — each line is whatever the most recent read returned.
