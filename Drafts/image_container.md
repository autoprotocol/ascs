#### **Title**
image_container

#### **Authorship**
Ben Miles ben@transcriptic.com

#### **Motivation**
Photography is a fairly common QC step such as checking for precipitation and can also be part of an analytical workflow such as looking for crystals in solutions. This instruction attempts to be agnostic about the container being imaged.

#### **Proposal**

This proposal proposes a new instruction, and one to supersede the redacted `image_plate` instruction.

```json
{
  "op": "image_container",
  "objects": Container,
  "view_point": ['above', 'side', 'below'],
  "mode": 'visible_light'
}
```

Example:

```json
{
  "op": "image_container",
  "objects": "my_384_flat_plate",
  "view_point": "above",
  "mode": "visible_light"
}
```

This example should yield a photograph of a 384 well plate from above using white light in the visible spectrum.

Mode is included to support cases such as epi-fluorescent imaging.

#### **Compatibility**
It is intended that `image_container` be a different instruction to a possible microscopy instruction in the future.
