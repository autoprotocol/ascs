#### **Description**
The `spectrophotometry` instruction encodes one or a series of plate reading steps executed on a single container with the same device.
This could be executed once, or at a defined interval, across some total duration.
There are 4 valid `mode`s (`absorbance`, `fluorescence`, `luminescence`, and `shake`) that each accept a different set of `mode_params`

#### **Specification**
{
  "op": "spectrophotometry",
  "dataref": String,
  "object": Container,
  "interval": Option<Time>,
  "num_intervals": Option<Int>,
  "temperature": Option<Temperature>,
  "shake_before": Option<{
    "duration": Time,
    "frequency": Option<Frequency>,
    "amplitude": Option<Length>,
    "path": Option<shake_path>
  }>,
  "groups": [
    Option<{
      "mode": "absorbance",
      "mode_params": {
        "wells": [Aliquot],
        "wavelength": [Length],
        "num_flashes": Option<Int>,
        "settle_time": Option<Time>,
        "read_position": Option<Enum(
          "top",
          "bottom"
        )>,
        "position_z": Option<{
          "manual": Option<{
            "displacement": Length,
            "reference": Enum(
              "plate_bottom",
              "plate_top",
              "well_bottom",
              "well_top"
            )
          }>,
          "calculated_from_wells": Option<{
            "wells": [Aliquot],
            "heuristic": Enum(
              "max_mean_read_without_saturation",
              "closest_length_without_saturation"
            )
          }>,
        }>
      }
    }>,
    Option<{
      "mode": "fluorescence",
      "mode_params": {
        "excitation": [{
            "shortpass": Option<Length>,
            "longpass": Option<Length>,
            "ideal": Option<Length>
        }],
        "emission": [{
            "shortpass": Option<Length>,
            "longpass": Option<Length>,
            "ideal": Option<Length>
        }],
        "num_flashes": Option<Int>,
        "settle_time": Option<Time>,
        "lag_time": Option<Time>,
        "integration_time": Option<Time>,
        "gain": Option<Float>,
        "read_position": Option<Enum(
          "top",
          "bottom"
        )>,
        "position_z": Option<{
          "manual": Option<{
            "displacement": Length,
            "reference": Enum(
              "plate_bottom",
              "plate_top",
              "well_bottom",
              "well_top"
            )
          }>,
          "calculated_from_wells": Option<{
            "wells": [Aliquot],
            "heuristic": Enum(
              "max_mean_read_without_saturation",
              "closest_length_without_saturation"
            )
          }>,
        }>
      }
    }>,
    Option<{
      "mode": "luminescence",
      "mode_params": {
        "wells": [Aliquot],
        "num_flashes": Option<Int>,
        "settle_time": Option<Time>,
        "integration_time": Option<Time>,
        "gain": Option<Float>,
        "read_position": Option<Enum(
          "top",
          "bottom"
        )>,
        "position_z": Option<{
          "manual": Option<{
            "displacement": Length,
            "reference": Enum(
              "plate_bottom",
              "plate_top",
              "well_bottom",
              "well_top"
            )
          }>,
          "calculated_from_wells": Option<{
            "wells": [Aliquot],
            "heuristic": Enum(
              "max_mean_read_without_saturation",
              "closest_length_without_saturation"
            )
          }>,
      }
    }>,
    Option<{
      "mode": "shake",
      "mode_params": {
        "duration": Option<Time>,
        "frequency": Option<Frequency>,
        "amplitude": Option<Length>,
        "path": Option<shake_path>
      }
    }>
  ]
}
