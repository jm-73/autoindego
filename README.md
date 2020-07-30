# indego-package

Home Assistant package for the Custom Component for Bosch Indego Lawn Mower. This package contains automations for:
Mowing schedule 
Set your app to manual and have the package automation mow your lawn 3 times a week.
Rain protection
With a rain sensor (local or cloud based) prevent the mower from working in rain.
Lightning protection
With a lightning sensor (local or cloud) the package sends the lawn in the lawn when thunder strikes are detected. Return to dock when thunder lightning are over.

## Installation

### Prerequesties
Required:
Home Asisstant 0.113 or newer (may work on older Home Assistant, not tested).
HACS Bosch Indego custom component.
Optional:


## Installation
In your configutaion.yaml file:
```
homeassistant:
  packages: !include_dir_named packages
```

## Configuration
Ajust the templates for your mower, the lightning and rain sensor.
``` yaml
#indego.yaml
indego:
#Required
  username: !secret indego_username
  password: !secret indego_password
  id:       !secret indego_id
#Optional
  name:     Indego
```

## Usage

### Entities


## Examples
Creating automation in HA gui:

Example for automations.yaml:

``` yaml
# automations.yaml
- id: '1564475250261'
  alias: Mower start
  trigger:
  - at: '10:30'
    platform: time
  condition: []
  action:
  - data:
      command: mow
    service: indego.command
```

## Debugging
To debug the automations, please see your homeassistant.log and the Logbook in Home Assistant.

## Contribution
If you experience any problems or if you have ideas about the automation of mowers, please feel free to write an issue. All suggestions are welcome!

## Issues
If you experience issues/bugs with this the best way to report them is to open an issue in **this** repo.

[Issue link](https://github.com/jm-73/indego-package/issues)

## More information

For more information about the Bosch Indego Home Assistant integration, join the Discord channel:
https://discord.gg/aD33GsP

<a href="https://www.buymeacoffee.com/jm73" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>
