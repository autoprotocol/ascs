#### **Description**
The `provision` instruction encodes adding some amount of an external resource to an aliquot or series of aliquots.

#### **Specification**
{
  "op": "provision",
  "resource_id": String,
  "measurement_mode": Option<Enum(
    "mass",
    "volume"
  )>
  "to": [
    Option<{
      "well": Aliquot,
      "volume": Volume,
      "dispense_velocity": Option<VolumeFlow>,
      "mix_after": Option<{
        "volume" Volume,
        "repetitions": Int,
        "velocity": Option<VolumeFlow>
      }>
    }>,
    Option<{
      "well": Aliquot,
      "mass": Mass
    }>
  ]
}
