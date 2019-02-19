#### **Description**
The `liquid_handle` instruction acts as a framework to allow precise control over liquid handling parameters and express a broad range of liquid handling operations.

The liquid_handle operation is based around transporting volumes of liquid in and out of locations.
Each operation is a locations sequence of location with transports sequences specifying the list of volumes.
The position of device components may reset between elements of locations.
Transports within the same locations use the same consumables (i.e. tips in the case of air_displacement liquid handling).

#### **Specification**
{
  "op": "liquid_handle",
  "locations": [
    {        
      "location": Option<Aliquot>,
      "transports": Option<[
        {
          "volume": Option<Volume>,
          "pump_override_volume": Option<Volume>,
          "flowrate": Option<{
            "target": Option<VolumeFlow>,
            "initial": Option<VolumeFlow>,
            "cutoff": Option<VolumeFlow>,
            "acceleration": Option<
              VolumeAcceleration
            >,
            "deceleration": Option<
              VolumeAcceleration
            >
          }>,
          "delay_time": Option<Time>,
          "mode_params": Option<{
            "liquid_class": Option<Enum(
              "air",
              "default"
            )>,
            "tip_position": Option<{
              "position_x": Option<{
                "position": Option<Float>,
                "move_rate": Option<{
                  "target": Option<Velocity>,
                  "acceleration": Option<
                    Acceleration
                  >
                }>
              }>,
              "position_y": Option<{
                "position": Option<Float>,
                "move_rate": Option<{
                  "target": Option<Velocity>,
                  "acceleration": Option<
                    Acceleration
                  >
                }>
              }>,
              "position_z": Option<{
                "offset": Option<Length>,
                "move_rate": Option<{
                  "target": Option<Velocity>,
                  "acceleration": Option<
                    Acceleration
                  >
                }>,
                "reference": Option<Enum(
                  "well_top",
                  "well_bottom",
                  "liquid_surface",
                  "preceding_position"
                )>,
                "detection": Option<{
                  "method": Option<Enum(
                    "tracked",
                    "pressure",
                    "capacitance"
                  )>,
                  "threshold": Option<Enum(
                    "pressure",
                    "capacitance"
                  )>,
                  "duration": Option<Time>,
                  "fallback": Option<position_z>
                }>
              }>
            }
          }>
        }
      ]>,
      "temperature": Option<Temperature>
    }
  ],
  "mode": Option<Enum(
    "air_displacement",
    "dispense"
  )>
  "mode_params": Option<{
    "tip_type": Option<String>
  }>,
  "shape": Option<{
    "rows": Int,
    "columns": Int,
    "format": Option<Enum("SBS96", "SBS384")>
  }>
}
