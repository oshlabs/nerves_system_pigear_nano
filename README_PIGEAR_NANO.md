This document contains information about the changes that were made for the PiGear Nano

![PiGear Nano image](assets/images/pigear-nano.jpg)

---

Forked from https://github.com/nerves-project/nerves_system_rpi4

Tag v1.22.2 / git rev 8ba745a

[Changes from tag v1.22.2 to branch pigear_nano](https://github.com/oshlabs/nerves_system_pigear_nano/compare/v1.22.2..pigear_nano)

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

Added iproute2 package from Buildroot so that type and speed can be set as follows:
```
cmd "ip link set can0 type can bitrate 250000"
cmd "ip link set up can0"
```

---

No binary artifact is uploaded yet for this nerves system, therefore use the following procedure to use it:
```
cd src/
git clone --branch pigear_nano https://github.com/oshlabs/nerves_system_pigear_nano
mix nerves.new test_pgn
cd test_pgn
```

Then edit mix.exs and perform the following steps:
* Add `:pigear_nano` to `@all_targets` list
* In the `defp deps` fuction body, add the following:
```
      {:nerves_system_pigear_nano,
       path: "../nerves_system_pigear_nano",
       runtime: false,
       targets: :pigear_nano,
       nerves: [compile: true]}
```

Then export the target to be `pigear_nano` as follows:
```
export MIX_TARGET=pigear_nano
```

And build your firmware:
```
mix firmware
```

This will take quite a while the first time, since it'll recompile the whole customized nerves system as well. The second run will go quicker as it can take the binaries from the sibling `../nerves_system_pigear_nano` directory.

Finally burn..
```
mix burn
```

..or upload as usual
```
mix upload
```

---

External references:
* https://hexdocs.pm/nerves/advanced-configuration.html#target-specific-configuration
* https://hexdocs.pm/nerves/targets.html
* https://hexdocs.pm/nerves/systems.html
* https://hexdocs.pm/nerves/customizing-systems.html
* https://www.uugear.com/doc/PiGearNano_UserManual.pdf
* https://labzero.com/blog/including-a-device-tree-overlay-in-an-elixir-nerves-project
* https://github.com/nerves-project/nerves/blob/main/docs/Advanced%20Configuration.md
* https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/configuration/device-tree.adoc
* http://velep.com/archives/1186.html
