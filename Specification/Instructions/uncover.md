#### **Description**
Containers must be covered or sealed for storage, incubation, and centrifugation operations (among others).
Many instructions including liquid handling operations require that a container be uncovered before use.
`store_lid` indicates that the lid should be saved for some subsequent `cover` instruction with `retrieve_lid`.

#### **Specification**
{
  "op": "uncover",
  "object": Container,
  "store_lid": Option<Boolean>
}
