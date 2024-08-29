# nice_view_custom_peripheral

A custom version of the nice_view shield that implements an animated corro graphic on the peripheral board's nice!view display

Theoretically compatible with all nice!nano nice!view boards.

## Usage

To use this module, first add it to your config/west.yml by adding a new entry to remotes and projects:

```yml
manifest:
  remotes:
      # zmk official
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: gpeye #new entry
      url-base: https://github.com/GPeye #new entry
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: zmk-periph-urchin
      remote: gpeye
      revision: main
  self:
    path: config
```

Now simply swap out the nice_view shield on the board for the custom one in the build.yaml file. You only need to do this for the right side as the left will be identical to the stock nice_view:

```yml
---
include:
  - board: nice_nano_v2
    shield: urchin_left nice_view_adapter  nice_view
  - board: nice_nano_v2
    shield: urchin_right nice_view_adapter nice_view_custom_peripheral #custom shield
  - board: nice_nano_v2
    shield: settings_reset
```