# Data

Multiple wires or signals can carry information, in a digital space we call these `bits`. The simpliest representation of `bit` information is a numerical representation.

*Connecting a calculator touchpad to a processor*
```discovery
Brute force use 13 wires: 0-9+-=, costly
use wire a bits
1 bit has 2 combinations, not enough
2 bits has 4 combinations, not enough
3 bits have 8 combinations, not enough
4 bits has 16 combination, which is enough
```

## Binary - base2
Bits are represented in base2 as a `0:1` number sequence with one side the `least significant bit (LSB)`, and the other side the `most significant bit (MSB)`.

`0010` is an example of the number `2`.

The normal number system of `base10[0:9]` and `base2[0:1]` are different representations of the same number line value, so all math functions still work. 

*Example of math with binary*
```example
base10: 3 + 4 = 7
base2: 0011 + 0100 = 0111
```

## Hexadecimal - base16
Bit representation in `base2[0:1]` is verbose, so we use a 4 bit grouping (example: `0101`), and represent it as `base16[0:9,A:F]`.

4 bits | Hex | 4 bits | Hex
--- | --- | --- | ---
0000 | 0 | 1000 | 8
0001 | 1 | 1001 | 9
0010 | 2 | 1010 | A
0011 | 3 | 1011 | B
0100 | 4 | 1100 | C
0101 | 5 | 1101 | D
0110 | 6 | 1110 | E
0111 | 7 | 1111 | F

*Example of math with hex*
```example
3 + 4 = 7
in hex is:
3 + 9 = C

another example
1F + 3 = 22
```

## Alphanumeric
Numbers have been represented with 4bits providing only 16 possible combinations, combining two 4bit groups provides 256 possible combinations which is more than enough for: numbers, punctuation, an upper and lower alphabet and extra space for more symbols.

An international standard mapping from number to letter was created called the `American Standard Code for Information Interchange (ASCII)`. 

With `ASCII` we can encode letters to numbers, store or transfer those numbers to the otherside of the world, and print those same letters back out. 

Chinese has way more then 256 characters, and other languages have there own special characters, so the `Unicode Standard` was created. Each letter represented by two bytes with a possible combination of 65,536,more than enough for all international languages.

## Signed and unsigned numbers
Thus far we have represented positive or unsigned numbers, however if a negative number is required the fact that the number is negative needs to be identified someplace.

`Ones' complement`, and `Two's complement` are two such encoding processes.

[Ones' complement](https://en.wikipedia.org/wiki/Ones%27_complement) - first bit represents sign, inverted value

Value | One's Complement | Unsigned
--- | --- | ---
-127 | 1000 0000 | 128
-126 | 1000 0001 | 129
-2 | 1111 1101 | 253
-1 | 1111 1110 | 254
-0 | 1111 1111 | 255
0 | 0000 0000 | 0
1 | 0000 0001 | 1
2 | 0000 0010 | 2
126 | 0111 1110 | 126
127 | 0111 1111 | 127

[Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) - 1 + first bit represents sign, inverted value

Value | Two's Complement | Unsigned
--- | --- | ---
−128 | 1000 0000 | 128
−127 | 1000 0001 | 129
−126 | 1000 0010 | 130
−2 | 1111 1110 | 254
−1 | 1111 1111 | 255
0 | 0000 0000 | 0
1 | 0000 0001 | 1
2 | 0000 0010 | 2
126 | 0111 1110 | 126
127 | 0111 1111 | 127


## Decimal
TBD

## Floating-point numbers
TBD

## Primitives
We need a way construct data structures. Primitives are the smallest data block, like lego blocks, and are in 1, 2, 4 and 8 length blocks.

The `byte` is typically the smallest unit, like an atom, and represents 8bits.

Name | Signed | Name | Unsigned | Storage
--- | --- | --- | --- | ---
`sbyte` | -126 to +127 | `byte` | 0 to 255 | 1 byte (8bits)
`short` | -32,768 to 32,767 | `ushort` | 0 to 65,535 | 2 bytes (16bits)
`int` | -2,147,483,648 to 2,147,483,647 | `uint` | 0 to 4,294,967,295 | 4 bytes (32bits)
`long` | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | `ulong` | 0 to 18,446,744,073,709,551,615 | 8 bytes (64bits)

Name | Signed | Storage
--- | --- | ---
`single` | 1.175494351 E - 38 to 3.402823466 E + 38 | 4 bytes (32bits)
`double` | 2.2250738585072014 E - 308 to 1.7976931348623158 E + 308 | 8 bytes (64bits)

## Records
New custom named types can be created by combining primitives, or previously defined Record types, creating complex data structures.

Similar to lego blocks, preassembled lego structures can be reused to speed up assembly while simpifiying the overrall design. Records provide the same function in data structures.

## Verification Digests
used for verifying a block of data

Name | Description
--- | ---
`crc` | A cyclic redundancy check is an error-detecting code commonly used in digital networks and storage devices to detect accidental changes to digital data.
`md5` | The MD5 message-digest algorithm is a cryptographically broken but still widely used hash function producing a 128-bit hash value.
`sha1`, `sha256` | In cryptography, SHA-1 is a cryptographically broken but still widely used hash function which takes an input and produces a 160-bit hash value known as a message digest.

---
## Glossary
Name | Description
--- | ---
`bit` | single bit of a data
`byte` | 8 bits
`word` | 2 bytes
`dword` | Double Word - 2 words
`qword` | Quad Word - 4 words
`signed` | A possibly signed number
`unsigned` | A number which can never be signed
`integer`, `whole`, `number` | A standard whole number
`decimal` | A number with a fractional part (ex: 1.5)
`float`, `double`, `single`, `real` | A number with a fractional part which floats (ex: 1.5)
`record`, `struct`, `class` | A data structure comprised of primatives or other records