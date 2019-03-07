#### **Description**
Time constraints encode a temporal relationship between two time points, `from` and `to`.

Each of the time points must specify exactly one of their optional fields.
`ref_start` and `ref_end` encode the points at which a Container leaves its origin and enters its destiny respectively.
`instruction_start` and `instruction_end` encode the points at the beginning and end of an instruction's execution; the instruction is represented by its 0-indexed position within the instructions list.

Each time constraint may include any combination of the `less_than`, `more_than`, and `ideal` fields.
`less_than` and `more_than` constraints encode the minimum and maximum amount of time that is allowable between the two time points.
`ideal` constraints encode the intended timing between two time points as well as the `optimization_cost` by which these fields should be weighted.

#### **Specification**
{
  "time_constraints": Option<[
    {
      "from": {
        "ref_start": Option<Container>,
        "ref_end": Option<Container>,
        "instruction_start": Option<Int>,
        "instruction_end": Option<Int>
      },
      "to": {
        "ref_start": Option<Container>,
        "ref_end": Option<Container>,
        "instruction_start": Option<Int>,
        "instruction_end": Option<Int>
      },
      "less_than": Option<Time>,
      "more_than": Option<Time>,
      "ideal": Option<{
        "value": Time,
        "optimization_cost": Option<Enum(
          "linear",
          "squared",
          "exponential"
        )>
      }>
    }
  ]>
}
