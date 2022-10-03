# ISA - INSTRUCTION LEVEL ARCHITECTURE #


## CPU - Central Processing Unit

a cpu is considered a load/store machine. It can only remember a few things. so it contantly needs to load from memory, preform an action, and store the result back to memory.

## MEMORY

[Memory segmentation](https://en.wikipedia.org/wiki/X86_memory_segmentation)

memory is broken into L1-L4 which is on the cpu, and system memory which is off the cpu.

L1-L4 are for the cpu data cache stream which represents a small amount of of cached system memory

system memory is made up of a large phyical address space. and sub-divided into logical memory spaces using segment registers below.

segment:offset so i can move my logical memory around on the phyical memory.

## REGISTERS

the cpu registry file represents the small amount of data that the cpu can remember at any one time.
note: the segment registers and a few others are included in this.

32bit vs 64bit
  - AX - 32bits
  - EAX - 64bits

### SEGMENTS
- CS - code segment
- DS - data segment
- ES - extra segment
- SS - stack segment
- FS - ignore
- GS - ignore

### GENERAL PURPOSE
- AX - accumulator
- BX - base
- CX - count
- DX - data

- broken down into High and Low, XH and XL respectivly.
  - AH - upper 16bits
  - AL - lower 16bits

#### COPY/COMPARE
- SI - source index
- DI - destination index

#### STACK
- SP - stack pointer
- BP - base pointer

#### SPECIAL
- IP - instruction pointer
- FL - flags


## OPERATIONS ##

```asm
mov ax, 4
mov ax, [4]
mov bx, 4
mov ax, [bx]
mov ax, [bx + 1]
mov [bx + 1], ax
```

```asm
add ax, 1
inc ax
dec ax
mul ax, 4
div ax, 4
```

```asm
call
ret
jmp
```

```asm
cmp ax, 3
jz - jump if zero
je - jump if equal
jg - jump if greater then
jt - jump if less then
jnz - jump if zero
jne - jump if equal
jng - jump if greater then
jnt - jump if less then
```

```asm
pop
push
```

## STACK
- stack is a way to store values on the "memory stack" pointed to by SS:ESP.
- push 3 - adds the number three to the stack
- pop ax - returns the number three from the stack into the ax register


## NAME ME
- SISD - Single Instruction, Single Data
- SIMD - Single Instruction, Multiple Data (SSE, AVX)
- SIMT - Single Instruction, Multiple Thread (GPU)