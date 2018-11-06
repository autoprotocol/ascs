#### **Title**
Change `object` field of `measure_mass` instruction


#### **Authorship**
Yang Choo <yang@transcriptic.com>

Varun Kanwar <varun@transcriptic.com>


#### **Motivation**
Measuring a list of containers with a weighing scale is not well-defined and doesn't fit into the usual modality of a scale. An instruction should be made as modular and encapsulated as possible, and reflect a single operation. 
Specifically for this case, if we interpret a list of container measurements as measuring each container sequentially, that makes it hard and ambiguous to handle any failure that happens within that sequence of measurements.


It would make more sense and simplify things if we instead just measured the mass of a single container and return a single dataref associated with the container.


#### **Proposal**
```
{
    "op": "measure_mass",
    "object": ["container"], -> "object": container,
    "dataref": string
}
```


#### **Execution**
The new instruction now looks like:
```
{
    "op": "measure_mass",
    "object": container,
    "dataref": string
}
```


The expected output is up to the vendor to decide, but should ideally include the mean and standard deviation of the measured mass.


#### **Compatibility**
This ASC changes the acceptable values for an existing field.


This is NOT backwards compatible (however, from a search through the database, all the existing object fields only contain a single container except for the initial test runs).


To make it backwards compatible, we could keep the same format, but enforce a check that the length of the list has to be one. We'll prefer not to however, since it'll be much clearer at that point if we define the input-type to not be a list, but a single container.
