# Title
Add `dispense` mode to `liquid_handle` instruction

# Authorship
Rhys Ormond <rhys@transcriptic.com>

# Motivation
Devices such as reagent dispensers are configurable in many of the same ways that channel-based `air_displacement` liquid handlers are. The primary difference between them is a the concept of a flow of liquid between two aliquots.

# Proposal
We propose the `dispense` mode for the `liquid_handle` instruction to represent the mode of liquid handling used by devices such as reagent dispensers.

This mode follows the same general structure of `air_displacement` differing primarily in how locations are interpreted. In `dispense` the first location referenced is always the source aliquot. All other locations that reference aliquots are destinations. Locations with no aliquot specified indicate a waste position.

The aspirated (negative) volume in the source location must equal the total volume dispense across all other locations.


```json
{
  "op": "liquid_handle",
  "locations": [
    {
      "location": aliquot,
      "transports": [
        {
          "volume": volume  // negative for source aliquot
        }
      ]
    },
    {
      "location": null,  // no location for dispense into waste
      "transports": [
        {
          "volume": volume  // positive for destination
        }
      ]
    },
    {
      "location": aliquot,
      "transports": [
        {
          "volume": volume  // positive for destination,
          /**
            *Unless otherwise specified all other parameters within transports are optional
            */
          "pump_override_volume": volume,
          "flowrate": {
          // target is required for flowrate
          "target": flowrate,
            "initial": flowrate,
            "cutoff": flowrate,
            "acceleration": volumeAcceleration,
            "deceleration": volumeAcceleration
          },
          “delay_time”: time,
          "mode_params": {
            "volume_resolution": volume,
            "liquid_class": Enum("air", "default"),
            "tip_position": {
              "position_x": {
                "position": float,
                "move_rate": {
                  "target": speed,
                  "acceleration": acceleration
                }
              },
              "position_y": {
                "position": float,
                "move_rate": {
                  "target": speed,
                  "acceleration": acceleration
                }
              },
              "position_z": {
                "offset": distance,
                "move_rate": {
                  "target": speed,
                  "acceleration": acceleration
                },
                "reference": Enum(
                  "well_top",
                  "well_bottom",
                  "preceding_position"
                )
              }
            }
          }
        }
      ],
      “temperature”: temperature
    }
  ],
  "shape": {
    "rows": int,  // optional
    "columns": int,  // optional
    "format": enum("SBS96", “SBS384”)  // optional
  },  // optional
  "mode": "dispense"
}
```

# Compatibility
This ASC specifies a new mode for an existing instruction and should be entirely backwards compatible.

