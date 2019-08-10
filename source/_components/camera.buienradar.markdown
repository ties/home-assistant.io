---
title: "Buienradar Camera"
description: "Instructions on how to integrate buienradar.nl radar image as camera within Home Assistant."
logo: buienradar.png
ha_category:
  - Camera
ha_release: 0.95
ha_iot_class: Cloud Polling
---

The `buienradar` platform uses [buienradar.nl](http://buienradar.nl/) as a
source for the last rain radar map. The overview image of the whole of the
Netherlands is loaded and shown as a camera in Home Assistant.

Internally this component uses the radar map image as
[documented](https://www.buienradar.nl/overbuienradar/gratis-weerdata) on
buienradar.nl. The downloaded image is cached to prevent Home Assistant from
making a new request to buienradar.nl multiple times a minute when Home Assistant
checks for new stills from the camera.

To add `buienradar` camera to Home Assistant, add the following section to your
`configuration.yaml` file:
```yaml
# Example configuration.yaml entry
camera:
  - platform: buienradar
```

{% configuration %}
name:
  description: You can (optionally) specify the name of the camera. The name
    will be shown in the user interface below the radar image.
  required: false
  type: string
dimension:
  description: Size of the image to be loaded from buienradar.nl
    (120 to 700 pixels)
  required: false
  default: 512
  type: integer
delta:
  description: Time interval in seconds between image updates
  required: false
  default: 600
  type: integer
{% endconfiguration %}

### The `name` Variable

If you specify a name, the camera will get this name as its label. A slugified
version of the name will be used as the name of the entity.

With the default of "Buienradar loop" the entity name becomes
`camera.buienradar_loop`.

<div class='note'>

This camera platform is configured independently from the Buienradar [buienradar.weather](/components/weather.buienradar) and [buienradar.sensor](/components/sensor.buienradar) platform.

For the best experience, combine the camera with one of these platforms.

</div>

[Usage statement:](https://www.buienradar.nl/overbuienradar/gratis-weerdata)
>Buienradar makes free weather-data available for use by individuals and businesses (website/intranet). The use of the weather-data is allowed for **non-commercial purposes**. Please refer to the full usage statement linked above to confirm your usage or to request permission.
