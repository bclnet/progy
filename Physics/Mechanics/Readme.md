# Mechanics
*Water, steam and electricity*

Early people mechanized water to perform work such as grinding grain in a River Mill. To overcome the limitations of water we moved to steam which could be viewed as a high pressure water source and mechanized steam similarly. To overcome the limitations of steam we moved to electrons which could be viewed as steam and mechanized similarly.

## [Hydraulic analogy](http://en.wikipedia.org/wiki/Hydraulic_analogy)

Electricity and the way we utilize it is conceptualized similarly to the water is managed and utilized.

Both water and electricty must flow from a `Source` to a `Drain`, when these are connected to allow for a return path a `Circuit` is created. In electronics `negative (-)` represents a source and `positive (+)` represents a drain with `negative (-)` flowing to `positive (+)`.

*Electronic circuit*
```define
An electronic circuit is composed of individual electronic components, such as resistors, transistors, capacitors, inductors and diodes, connected by conductive wires or traces through which electric current can flow. 
```

*Mapping of elements in water and their equivalent in electronics*

Water element | Electronics element
--- | ---
Pipes | Wires
Water tower | Capacitor
Dam-Constraints | Resistor
Shutoff valve | Switch
Variable valve | Variable Resistor

*Complexities (optional)*
```define
Network of pipes have different pressures based on pipe sizes or valve status or inline constraints, networks become complicated.
Rouge EM instruduced voltages randomly anywhere.
Longer running wires also act as capactators.
```


## Measurement
Its important to have a means of measurment and instrumentation.

As this relates to water, there is the pressure (PSI) in the hose, the amount of water in the hose, and the resistance to water movement the hose has. Similary this would relate to, the electronic pressure in a wire, the electronic volume in the wire, and the resistance of the wire. These measurements are: `Volts (V)`, `Amps (I)` and `Ohms (R)` respectivly. 

Because the diameter or pressure of water in the hose can change resulting in a the same water moved. A unified mesurement of power called `Watts (W)` exists as the product of `Volts (V)` and `Amps (I)` and mesures the power of the circuit.

Volts are always measured between two points since it is the pressure between those two points.

Omhs are governed my [Ohm's law](http://en.wikipedia.org/wiki/Ohm%27s_law).


```example
Volts can be though of as the potential energy in a dropped ball, and Amps would be the size of the ball.
```

Name | Description | Symbol
--- | --- | ---
Watts | unitized measure of power | W = IV
Volts | measures electronic presure | V
Amps | measures electronic volume | I
Ohms | measures electronic resistance | R


## Digital Abstraction
The real world is complex and everchanging, and system design becomes complex and hard to engineer.

Instead engineers operate in a fantasy world, a `Digital Abstraction` of the real world instead of the real world, where these complexies no longer exists. 

In this new world: Voltage, amperage, resistance, inductance, capacitance, radiation, presure, temperature no longer exist. Wires exist in only one of two states: On and Off, or 0 and 1 respectively.

When refering to real world principals or finite values, we use the term `Analog` vs the `Digital` term for the fantasy world. 


```
Rules that translate digital to analog because we still exist in analog world
Lets say 0.0-0.25 volts is OFF and 0.45-1.0 is ON
Each circuit is up to three hops away from power source. So we don't get pressure loss going through too many circuits
```

## Continual Advancement
The materials, techiques and technologies used in these circuts are continually advancing as we find newer and better approaches.

Some of these advances:
- Strained silicon
- High K
- FinFET
- RibbonFET (GAA)