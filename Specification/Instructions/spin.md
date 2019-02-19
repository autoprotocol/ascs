#### **Description**
The `spin` instruction is used to represent a series of centrifugation steps.
The `inward` and `outward` `flow_direction` encodes spinning the contents into or out of of a container respectively.
The operation is repeated with the appropriate direction for each element in `spin_directions`.

#### **Specification**
{
  "op": "spin",
  "object": Container,
  "acceleration": Acceleration,
  "duration": Time,
  "flow_direction": Option<Enum(
    "inwards",
    "outwards"
  )>,
  "spin_direction": [
    Enum("cw", "ccw")
  ]
}
