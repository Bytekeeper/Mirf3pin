# Mirf3pin
Mirf library modification which only needs 3 data pins on your arduino.

"Copied" from http://nerdralph.blogspot.de/2014/01/nrf24l01-control-with-3-attiny85-pins.html
Use the circuit as described there. For Arduino Nano you won't need the addition LED for bring down 5V to 3,3V just
connect directly to 3,3V.

To use this library you'll need to have the original Mirf library installed as well!

Example to use retrieve status, which should return "E" according to above's link (which it does if connected properly)
```
#include <SPI.h>
#include <nRF24L01.h>
#include <MirfSpiDriver.h>
#include <MirfHardwareSpiDriver.h>
#include <Mirf2.h>

void setup()
{
  Serial.begin(9600);

  Mirf2.spi = &MirfHardwareSpi;
  Mirf2.init();
}

void loop()
{
  uint8_t nrfStatus;
  delay(3000);
  Serial.print("\nMirf status: ");
  nrfStatus = Mirf2.getStatus();
  // do back-to-back getStatus to test if CSN goes high
  nrfStatus = Mirf2.getStatus();
  Serial.print(nrfStatus, HEX);
}
```
