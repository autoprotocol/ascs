Instruction and ref specification use the following common types.

#### Primitive Types
| Type             | Definition
|-                 |-
| **Boolean**      | `true` or `false`
| **Float**        | a floating point numeric value
| **Int**          | an integer numeric value
| **String**       | any sequence of utf-encoded characters bounded with `"`

#### Derived Types
| Type                        | Example Value           | Definition
|-                            |-                        |-
| **Aliquot**                 | `"growth_plate/A1"`     | an Autoprotocol container and a well index delimited with a `/` represented as a String
| **Container**               | `"growth_plate"`        | an Autoprotocol container referenced in the refs section of the protocol represented as a String
| **Quantity**  e.g. `Volume` | `"5:microliters"`       | a magnitude and a unit delimited with a `:` represented as a String
| **Compound**                | `"InChI=1S/CH4/h1H4"`   | a chemical compound definition, following the IUPAC Standard InChI format.

#### Type Wrappers
| Syntax             | Example Specification | Definition
|-                   |-                      |-
| **Enum(..)**       | `Enum("one, "two")`   | any one of the enclosed values
| **Option\<Type\>** | `Option<String>`      | either be the enclosed Type or `null`
