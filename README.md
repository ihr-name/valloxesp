# Vallox ESPHome component
Vallox SE ventilation control software for ESPHome (and thus Home Assistant)

> [!NOTE]
> ### About this fork
> [mickut/valloxesp](https://github.com/mickut/valloxesp) **+ one commit — nothing else.**
>
> - **All the heavy lifting is mickut's:** ESPHome 2026 compatibility, dropping `<Arduino.h>` (which is what makes `esp-idf` usable), and rewriting the UART into a non-blocking state machine with a prioritised send queue.
> - **This fork adds a single fix:** custom fan modes are registered on the `Climate` entity instead of on `ClimateTraits` — deprecated in ESPHome 2026.5.0, **removed in 2026.11.0**. Behaviour unchanged.

Builds with zero warnings on ESPHome 2026.7.3 / `esp32dev`, under both `arduino` and
`esp-idf`. Running on a **Vallox ValloPlus 500 SE**.

Not to be confused with [kotope/valloxesp](https://github.com/kotope/valloxesp), the
original, which is unmaintained since May 2024 and no longer builds on current
ESPHome. Migrating from it: `extra_func` removed, `switch_remaining` added.

# Hardware
See guide at https://www.creatingsmarthome.com/?p=73

## Should work with any device using the VALLOX DIGIT bus protocol over RS485 including:
- Vallox 096 SE
- Vallox 110 SE
- Vallox 121 SE (version without front heating module)
- Vallox 121 SE (version with front heating)
- Vallox 150 SE
- Vallox 270 SE
- Vallox Digit SE
- Vallox Digit SE 2
- Vallox ValloPlus 350 SE
- Vallox ValloPlus SE 500

# Home Assistant components
Contained entities:
* climate: Climate entity with Off/Fan Only/Heating operation mode, fan speed control, target temperature control
* All additional sensors, number, button, etc. are optional and can be included as needed.
* If you need a specific feature that is not included let me know, adding it should be straightforward.

# Configuration
Copy content of example_vallox.yaml to your esphome configuration for your device.
Adjust UART pins (RX/TX) as used with your device.
