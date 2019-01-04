# bigInteger
Background

Integer.MAX_VALUE is the maximum value of a Java int: 2147483647. If you want to work with even bigger integers, you have the option of using the type long, which has the maximum value of Long.MAX_VALUE = 9223372036854775807.

But what if this is not enough? What if you are working on something like an astronomy application, and need to keep track of things such as number of stars in the universe? This is of the order of 1023, larger than the maximum long value. For situations like this, you need to be able to work with an integer type that can hold arbitrarily large or small positive and negative values, with any number of digits. There is no built-in type in the language for this, so you need to craft your own. In this assignment, we do exactly this, by implementing a class called BigInteger, with a representative small set of operations.

The trick is to store an integer as a linked list of digits. For example, the integer 754 will be stored as:

   4 -> 5 -> 7
Why are the digits stored backward? It's because computations such as adding or multiplying big integers are easier to do if the linked list stores digits in ascending order of positional value. So the least significant digit is in the first node of the linked list, and the most significant digit is in the last node.
This is a simple linked list, NOT circular, with a front pointer. The sign (positive or negative), is stored separately in a boolean field in the program.

Also, there can never be zeros at the end of the list. Such zeros will be insignificant. So, for instance, 00754 will be stored as:

   4 -> 5 -> 7 (NOT 4 -> 5 -> 7 -> 0 -> 0)
Consequently, the value 0 will be stored as an EMPTY LINKED LIST. The number of digits is 0, and it is not negative.
