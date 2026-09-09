# hexhound-flasher

Browser-based flasher for [HexHound](https://github.com/h4d35x0/hexhound), a
virtual pet for ESP32 boards that evolves by doing real Wi-Fi and BLE
reconnaissance.

**Not live yet.** This repository is the publish target for the flasher page and
its firmware payload. Both are generated from the `web/` directory of the main
repository by `scripts/deploy_web_flasher.py`; nothing here is edited by hand.

## Why it is empty

The deploy is gated, deliberately, and both gates are currently closed:

- The firmware signing keys in the main repository are **development** keys
  whose private halves were generated on a developer machine. Anyone holding the
  OTA private half could sign firmware that a device accepts as genuine, which
  is the whole point OTA signing exists to prevent. The deploy script refuses to
  publish images built against such a key.
- The staged board set is incomplete, and the script refuses to publish a
  partial board picker rather than quietly ship one that is missing hardware.

Until release keys exist and a full board set is staged, build from source
instead: see the main repository's `README.md` and `docs/build-environments.md`.

## Flashing, once this is live

The page uses [ESP Web Tools](https://esphome.github.io/esp-web-tools/) and
needs a browser with Web Serial: Chrome or Edge on desktop. Pick your board,
plug it in, flash. The board picker is load-bearing, because several supported
images share a chip family and cannot be told apart automatically.
