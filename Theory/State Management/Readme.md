# State Management

Most programing at its root deals with `state` and the management of it.

`State` is an abstract term for data.
> a computer program stores data in variables, which represent storage locations in the computer's memory. **The contents of these memory locations, at any given point in the program's execution**, is called the program's `state`.

## Actual vs calcuated state

State should also be categorized into actual and calculated state, for instance while a persons birthday and age are information about a person, the birthday is `actual state`, while the persons age is a `calcuated state` from the birthday. 

In a storage system like a database, only `actual state` needs to be stored.

## State as a dimension

Another way to look at state is classify each symbol in 1, 2 or 3 dimensions.

* 1d - Variable, Scaler
* 2d - Array, List, Collection
* 3d - Dictionary, Map

example | symbol | dimension
--- | --- | ---
A persons name | name | 1d
All the people who showed today | people | 2d
The attributes of a single person | person | 3d