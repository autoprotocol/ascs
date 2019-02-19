#### **Description**
Containers must be covered or sealed for storage, incubation, and centrifugation operations (among others).
Seal `type`s have useful properties ranging from optical clarity to gas permeability.
Seals can be applied by either `thermal` or `adhesive` sealers which result in different seal integrity.
`thermal` seals can be applied with a range of temperatures and durations that can be optimized for different plate types.
Many instructions including liquid handling operations require that a container be uncovered before use.

#### **Specification**
{
  "op": "seal",
  "object": Container,
  "type": String,
  "mode": Option<Enum("thermal", "adhesive")>,
  "mode_params": Option<{
    "temperature": Option<Temperature>,
    "duration": Option<Time>
  }>
}
