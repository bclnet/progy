# Storage & Cache

Multiple way exist to store and retrieve values each with their pros and cons. Physical size, access speed, volitility and storage capacitance are some aspecs evaluated. Typically multiple storage types exist in series and data moves between them. 

## Random Access Memory (RAM)
`Random Access Memory (RAM)` is a class of memory used to store and retrieve data.

A modern computer will usally have these in series: Static Ram, then Dynamic Ram, then Non-volitile Ram.

Static ram is fast and small but with costly with extreamly small capacaties; think kilobytes. Its size allows static ram to exist directly inside the CPU.

Dynamic ram is physically larger and exists outside of the CPU as seperate compute elements, but can be manufactured with large capcaties cost effectly; think gigabytes. Its long distance from the CPU causes load and store operations to take longer; think driving to the store to get a soda.

Both static and dynamic ram both lose their memory when power is no longer applied. Non-volitle ram retains its memory but is slower to access, but can be manufactured with large capacties cost effectitly; think terabytes.

A file stores long term data in Non-volitle ram, then sections are accessed and placed in Dynamic ram, then placed in Static ram to perform functions on.

### Sram
Static ram. is the fastest but costliest storage. There's a way I can put two logic gates that feed their outputs to each other, so that they store a bit value on or off.  I can arrange these in huge fields with rows and columns like crops, and store large amounts of bits.

### Dram
Dynamic ram. A much smaller storage mechanism, and easier to reproduce. Allowing 1000s of times increase in storage capacity. Vast fields of draining wells. With a refresh process to check how empty and refill if partially filled. Also arranged in huge fields  with rows and columns like crops, allowing the storage of vast quantities of bits. 

### Ddram
Also called DDR or double dynamic ram. Uses the same technique as Dram but allows two reads and writes per access. The data wires to the memory chips have become the bottleneck. So DDR uses a half rise and half fall to double the bandwidth though the memory terminals. Everything else inside the package is similar to Dram.

### Nvram
Also called non volatile ram. Uses a floating charge inside the silicon to hold a value. Setting or clearing the charge as needed. Holds its value even when power has been removed.

### Platters
Spinning platters and a read/write head slide to magnetic islands on the platters changing the magnetism of that island to store a one or zero. Also holds its values when power has been removed.


## Cache
Information must be retried and stored from ram to be useful, but there are some access patterns that can be applied to make this for efficiate.

Think of this example:
You are at your desk and want a soda.
You go to the kitchen fridge and retrieve a soda.
An hour later you want another soda and go to the kitchen fridge to retrieve another soda.

Alternativly:
You are at your desk and want a soda.
You go to the kitchen fridge and retrieve a six pack of sodas and place them in a small desk fridge under your desk.
An hour later you want another soda and reach into the small fridge under your desk.

The small desk fridge is a cache to the kitchen fridge and instead of retrieving one soda you retrieve a bundle of sodas. Similary your kitchen fridge is a cache to the grocery store, which is a cache to the distribution center.


## Modern CPU Cache
Modern CPUS will have multiple caching layers between external ram and internal registry files. Data is pulled and cached through these layers in `cache lines` during each round trip to the next layer of cache, accelerating sequential read operations. Single threaded applications flush cache when written to, however extra care must be taken when read and write operations occur between multiple cpus or threads.

## Network Cache
Network application caches exist to pool memory resources between computers, acting as additional layers at the application level.