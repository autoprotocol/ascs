#### **Description**
Containers must be covered or sealed for storage, incubation, and centrifugation operations (among others).
Many instructions including liquid handling operations require that a container be uncovered before use.
`retrieve_lid` indicates that a lid previously saved by a `uncover` operation with `store_lid` should be used.

#### **Specification**
{
  "op": "cover",
  "object": Container,
  "lid": String,
  "retrieve_lid": Option<Boolean>
}
