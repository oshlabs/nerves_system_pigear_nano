This document contains information about the changes that were made for the PiGear Nano

---

Forked from https://github.com/nerves-project/nerves_system_rpi4
Tag 1.22.2 / git rev 8ba745a

---

Incorporate configuration and device-tree overlay as provided by UUGear
- https://www.uugear.com/product/pigear-nano/
- https://www.uugear.com/repo/PiGearNano/installPiGearNano.sh
- wget https://www.uugear.com/repo/PiGearNano/LATEST -O pgnano.zip

* I2C1 Device tree overlay (i2c1.dtbo)
* I2C6 Device tree overlay (i2c6.dtbo)
* UART3 Device tree overlay (uart3.dtbo)
* UART4 Device tree overlay (uart4.dtbo)
* UART5 Device tree overlay (uart5.dtbo)
* SPI1-1CS Device tree overlay (spi1-1cs.dtbo)
* MCP2515 Device tree overlay (mcp2515-can2.dtbo) - provided by UUGear
* MCP342X Device tree overlay (mcp342x.dtbo)

Added libgphoto2 package from Buildroot
