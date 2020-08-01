# indego-package

Home Assistant package for the Custom Component for Bosch Indego Lawn Mower. This package contains automations for:
## Mowing schedule 
Set your official Bosch Indego app to manual and let package automation mow your lawn 3 times a week.
## Rain protection
With a rain sensor (local or cloud based) prevent the mower from mowing the lawn when it is raining.
## Lightning protection
With a lightning sensor (local or cloud) the package sends the mower to stay in the lawn when thunder strikes are detected. Return to dock when thunder lightning are over. This is to prevent the mower from getting damaged when it is connected to the docking station and the guidance cable. When disaster strikes, the guidance wire will pick up some high voltage that potentially could ruin your mower.

# Installation

## Prerequesites
### Required
Home Asisstant 0.113 or newer (may work on older Home Assistant, not tested).

HACS Bosch Indego custom component.

### Optional for lightning detection
HACS Blitzortung<br>
Local lightning sensor

### Optional for rain detection
OpenWeather<br>
YR<br>
DarkSky?<br>
HACS ???<br>
Local rain sensor

## Copy package file
Make sure your Home Assistant has a packages folder configured in your configutaion.yaml file:

```
homeassistant:
  packages: !include_dir_named packages
```

Place the indego.yaml file in the packages directory.

## Configuration
Ajust the templates for your mower, the lightning and rain sensor in the section sensor:
``` yaml
#indego.yaml
.
.
.
  ### Place your lightning sensor in the template here. Either local lightning sensor or cloud based services.
  - platform: template
    sensors:
      lightning_counter:
        value_template: "{{states.sensor.blitzortung_lightning_counter.state}}"
.
.
.
```

Ajust the rain sensor template for your Hoem Assistant instance.
``` yaml
#indego.yaml
.
.
.
  ### Place your rain sensor here. Either local sensor or cloud based services.
  - platform: template
    sensors:
      rain_counter:
        value_template: "{{states.sensor.rain_counter.state}}"
.
.
.
```

## Usage
The package creates:
5 automations
## Customizalbe automations
### Indego mow
Triggers three times a week. Adjust your schedule here!
## Do not mess with these automations
### Indego stop mow
Stops the mower after one completed mow.
### Indego stop mow session complete
Watches the input_boolean.mow_session_complete and ends the session whenever the boolean mow_session_complete turns to on.
### Indego check completed upper
Internal automation to check when the lawn is completed
### Indego Lightning protection trigger
Internal automation to detect lightning strikes from sensor.
### Indego Lightning protection de-trigger
Internal automation to detect when lightning has stopped.
### Indego lightning protection
Internal automation to send the mower out in the lawn when lightning is detected.
### Indego lightning protection
Internal automation to return the mower to the dock when lightning has stopped.


## input_boolean
## input_boolean user cofigured
### lawnstatus
This sensor should be used for automating when an scheduled mow can begin. For example, could be used with actionable trigger notifications to your cell when a scheduled mow is about to start.
## input_boolean system cofigured (do not change)
### completed_lower:
### completed_upper:
### mow_session_completed:
### lightning_protect:
### rain_protect:

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
