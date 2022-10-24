=========
Sign
=========

8	4	2	1				1
----------------			|
0	0	0	0				|
0	0	0	1				|
0	0	1	0				V
0	0	1	1				15


0000 --> 1111
	-0 vs 0
	
Determine amount of space needed for whole number using primi(a?)tives

=========
Bytes
=========

[] 						- 1 bit, or 8
[] [] 					- 2 bit, or 16
[] [] [] [] 			- 4 bit, or 32
[] [] [] [] [] [] [] [] - 8 bit, or 64


=========
Arrays
=========

[     ] A
[     ] B
[     ] C
 
 --or--
 
	A[3]
	
=========
Struct (way to handle multiple arrays)
=========

struct Month {
	int Players,
	int Wins,
	bool Pizza,
};

=========
Malloc - Memory Allocation
=========
(your program will manage for you)

I need 100 for my Struct, it goes and finds it
	Typically, you say I need X amount, but it provides more for you to play around in
	
	
[1] 	[2] 	[3] 	[4] 	[5] 		
[S]		[k]		[y]		[_]		+		[M] [o] [r] [e] [y] 
[] [] [] [] [] [] [] [] [] [] 


	LINKED LIST
		"Mapping" disparate memory boxes (they're not right next to each other)
		Slower to find
			[ ]
			 |---> [ ]
					|
					|
					V
				   [ ] ---> [ ]
	BINARY TREES
		[ ]
		 |
	[ ]------[ ]
	 |		  |
	----
	|  |
   [ ][ ]

	Good, but only left and right

	
=========
Requesting Blocks
=========
	16 GB of memory for needs
	16 TB of Database
		Can only provide in big blocks
		Binary trees don't work well in hard drives because of the way blocks are provided
		
	B TREES
		[ 1000 ]
			|		
			---------
					|
				[ 1000 ]
	Multiple lefts and rights

========
SQL Language
========

See Progy for types


Char(10)
[1234567890]
[SKY-------]

nvarchar(50), nvarchar(MAX)	--> this is what we use, it is unicode

[text] ---linked to ---- [this is text, lorem ipsum, etc.]
