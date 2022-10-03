# Silicon Engine : CPU
A cpu is considered a load/store machine. It can only remember a few things. so it contantly needs to load from memory, preform an action, and store the result back to memory.

## Computer Elements

**Registry File** - CPUs can only remeber and operate on a few stored values, these values are held in the registry file. 

**Memory** - memory is the larger storage that a cpu can access. phycial memory and virtual memory are handled seperatly, so phyical memory is accessed through pages of the virtual memory. note: virtual memory can be tremendously larger then available physical memory.

**Process/Application** - a running program assigned a main thread, and assigned a protected memory segment.

**Stack** - part of an applications memory segment with stack access symantics

**Heap** - part of an applications memory segment with random access symantics

**Segment** - part of the memory interface to enable memory segmentations

**Pages** - Accessable sections of memory through pages.

**Image** - The compiled software image for an application or its libraries, to be loaded into memory.

**Thread** - A timesliced virtual process

**Operating System** - An application service to access system resources, and launch new applications


## Other Services

**Storage** - Slower long term persistant storage

**Network** - Network interfaces for your application to interact with

**Video** - Video interfaces for your application to interfact with

**Audio** - Audio interfaces for your application to inter