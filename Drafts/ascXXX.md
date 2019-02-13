#### **Title**
Add `cover_state` field to `Ref` specification.

#### **Authorship**
Donald Dalton <donald@transcriptic.com>

#### **Motivation**
We should allow creation of `Refs` with initial cover states.

#### **Proposal**
Allow `Refs` to optionally specify an initial `cover` state from the set of cover types compatible with the corresponding container.

```
{
  "instructions": [...],
  "refs": {
    "<ref name>": {
      ...,
      /* optional */
      "cover": <type>,
      ...
    }
  }
}
```

Available cover types are specified by the vendor, examples include: `standard`, `universal`, `ultra-clear`, `foil`, `low_evaporation`, `breathable`.

#### **Compatibility**
This is entirely backwards compatible as only new parameters are added. Vendors should indicate if they are unable to respect any of the parameters.