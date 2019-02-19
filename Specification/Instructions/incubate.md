#### **Description**
The `incubate` instruction stores a sample in an incubator with the appropriate settings for a given duration.

#### **Specification**
{
  "op": "incubate",
  "object": Container,
  "where": Enum(
    "cold_20",
    "cold_4",
    "ambient",
    "warm_37"
  ),
  "duration": Time,
  "shaking": Boolean,
  "co2_percent": Option<Float>,
  "target_temperature": Option<Temperature>,
  "shaking_params": Option<{
    "frequency": Frequency,
    "path": Option<shake_path>,
    "amplitude": Option<Length>
  }>
}
