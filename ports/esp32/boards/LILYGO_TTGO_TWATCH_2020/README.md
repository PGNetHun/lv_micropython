# Board files for Lilygo TTGO T-Watch 2020 (V1/V2/V3)

## Prerequirements
- Clone repository following "Build instructions" section in  [root README](../../../../README.md)
- Setup ESP-IDF and build environment based on [README for the ESP32 port](../../README.md)

## Build the firmware
Go to the `ports/esp32` directory and execute:

```text
export PORT=<your serial port>
export BOARD=LILYGO_TWATCH_2020
esptool.py erase_flash && \
make submodules && \
make -j $(nproc) && \
make deploy
```

After the firmware is deployed to the device, and it is restarted, you should upload a `main.py` file which contains your program.
In your program you can import `ttgo` module, and call `init()` function to initialize the device (power, display, touch sensor and LVGL).

Example of `main.py` file:
```python
import ttgo
ttgo.init()

import lvgl as lv
scr = lv.obj()
btn = lv.btn(scr)
btn.align(lv.ALIGN.CENTER, 0, 0)
label = lv.label(btn)
label.set_text("Button")
lv.scr_load(scr)
```