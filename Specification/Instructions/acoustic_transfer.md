#### **Description**
Acoustic liquid handling uses acoustics to fly individual droplets from a source container to a destination one.
Most acoustic liquid handlers only support a discrete set of `droplet_size` and the `volume` field of each `transfer` must be a multiple of it.
`prevalidate_sources` is used to ensure that the source wells contain enough volume to successfully complete the transfer.
`source_volume_limits` are used to overwrite vendor-specified defaults for what volumes should pass prevalidation.

#### **Specification**
{
  "op": "acoustic_transfer",
  "droplet_size": Option<Volume>,
  "prevalidate_sources": Option<Boolean>,
  "groups": [
    {
      "transfer": [
        {
          "from": Aliquot,
          "to": Aliquot,
          "volume": Volume
        }
      ]
    }
  ],
  "source_volume_limits": Option<{
    "min": Option<Volume>,
    "max": Option<Volume>
  }>
}
