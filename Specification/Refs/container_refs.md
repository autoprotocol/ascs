#### **Description**
**Names**:
The `refs` field aliases Containers to descriptive Strings called refs.

**Origins**:
The `id` field is used to specify the unique identifier of an existing Container.
The `new` field is used to specify that this ref does not yet exist and what type of Container it should be.
These two fields are mutually exclusive.

**Destinies**:
The `discard` field indicates whether the ref should be discarded or not.
The `store` field indicates how a ref should be stored.
These two fields are mutually exclusive.

#### **Specification**
{
  "refs": {
    String: {
      "id": Option<String>,
      "new": Option<String>,
      "store": Option<{
        "where": Option<Enum(
          "cold_80",
          "cold_20",
          "cold_4",
          "ambient",
          "warm_30",
          "warm_37"
        )>
      }>,
      "discard": Option<Boolean>
    }
  }
}

