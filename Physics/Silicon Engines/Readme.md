# Silicon Engines

`Integrated circuits (IC)` are created with `Fabrication` techniques and result in transitors counts ranging from tens to trillions. An analogy to its sizes and complexity are like the following: a house, a skyscraper, a city, a metropolitan.

Growing transitor counts and complexity caused a categorization of these integrated circuits: Application Specific Integrated Circuit (ASIC), DSP, CPU, GPGPU and FPGA. 


## Application Specific Integrated Circuit (ASIC)
Custom application specific integrated circuits usually have limited softward defined logic and are a catch all to designs which do not fall into the other categories.

All silicon designs prior to microprocessors could be considered ASICs. After building lots of circuits


## Central Processing Unit (CPU)
After building a lot of houses, one realizes they are basically made up of bathrooms bedrooms kitchens and living rooms.

Sacrifice realtime and only use one room at a time, and you could build a meta house. With one bathroom, one bed room, one kitchen, and one living room. Add another room to sequence these. And a stream of bytes to tell u which room to use next. And u get virtually any combination of house you want with out having to rebuild.

This is what a microprocessor does. The rest is just trying to structure my house to be most efficient at using the rooms. Or predicting what will happen.

## General-purpose Graphics Processing Unit (GPGPU)
Different way of structuring the silicon.

In a CPU to paint a house white. You would have one guy paint every surface. GPU operations are usually redundant dividing up a screen lets say into 64 smaller screens. And performing an action on all 64 at one time. A GPU painting a house would have 64 guys, one for each wall that needs to be painted and each painting just their wall.

## Field-programmable Gate Array (FPGA)
A different approach.

Since logic gates are really just a table of ones and zeros with a result. Millions of tiny programmable elements which make virtual logic gates. And a way to programmatically interconnect them. Makes a ASIC that is dynamic. And runs in realtime. Sort of the best of both worlds.


## ISA
In each of these platforms there a language to program it. Also sometimes refered to as its ISA.

for a CPU for instance

```
MOV AX, 13h
MOV BX, 2
REPZ STOSW
```

## Continual Optimazations
The design of these continually evolving seeking the best balances of power, compute, heat and space

Some advancements are
- In-order vs Out-of-order Processing
- Branch Prediction
- Micro ops
- Hyper-threading
- Numa


## [Engine : CPU](/Cpu/)
Cpu