# esphome-templates

Reusable [ESPHome](https://esphome.io) package for **Seeed Studio XIAO ESP32-C6**
Bluetooth-proxy nodes (BLE room presence for Home Assistant).

## `seeed_xiao_c6_proxy.yaml`

Wi-Fi 6, status LED, BLE scanning + `bluetooth_proxy`, a **BLE Scan Profile**
select, and diagnostics — with the **antenna defaulted to the internal PCB
antenna** so it doesn't revert to the (unattached) external U.FL on reboot.

Adapted from
[DerekSeaman/ESPHome-Seeed-Xiao-ESP32-C6-Config](https://github.com/DerekSeaman/ESPHome-Seeed-Xiao-ESP32-C6-Config).
Changes: the hardcoded external-antenna `on_boot` block is removed, and the
"External Antenna" switch uses `restore_mode: RESTORE_DEFAULT_OFF` — it
defaults to internal and remembers your toggle across reboots. The switch has
an `id` (`sw_external_antenna`) and an **Active Antenna** sensor reports which
antenna is live.

## Use it

In your ESPHome Device Builder device YAML (the auto-generated one), add:

```yaml
packages:
  device:
    url: https://github.com/myst3k/esphome-templates
    ref: main
    file: seeed_xiao_c6_proxy.yaml
    refresh: always
```

The generated `esphome`/`esp32`/`logger`/`api`/`ota`/`wifi`/`captive_portal`
merge with this package — no other edits needed. If you ever solder on a U.FL
antenna, flip the "External Antenna" switch; it'll stick.
