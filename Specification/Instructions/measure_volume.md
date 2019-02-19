#### **Description**
The `measure_volume` instruction can be used to determine the volume of a sample.
The execution is vendor specific and may or may not consume a fraction of the sample. The accuracy of results is vendor specific.

#### **Specification**
{
  "op": "measure_volume",
  "object": [Aliquot],
  "dataref": String
}
