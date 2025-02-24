Download link :https://programming.engineering/product/ece-421-assignment-2-generics-in-rust/


# ECE-421-Assignment-2-Generics-in-RUST
ECE 421 Assignment 2: Generics in RUST
Rust Generics

Generics is the topic of generalizing types and functionalities to broader cases. Generics is useful as it helps reduce duplicated code. However, using generics requires taking great care to specify over which types a generic type is actually considered valid. The simplest and most common use of generics is for type parameters. For example, defining a generic function named myFunction that takes an argument T of any type:

fn myFunction<T>(arg: T) { … }

Although types in Rust are erased, generics are also reified. Consider the following code:

struct Bag<T> {

t: T,

}

fn main() {

let b = Bag { t: 42 };

}

A Bag<u8> is not the same type as a Bag<u32>. Although it implements the same methods, it has a different size.

Question 1: Rewrite the Bag struct to hold an array of 3 items of type T.

Question 2: Write a function named BagSize that takes a Bag as an input and returns the size of a Bag.

Test your function with the following code:

let b1 = Bag {items: [1u8, 2u8, 3u8], };

let b2 = Bag {items: [1u32, 2u32, 3u32], };

The code should give the following output:

size of First Bag = 3 bytes

size of Second Bag = 12 bytes

Question 3: Rewrite the code for b1 and b2 without using any generics to produce the same output.

[Hint: you will have to duplicate a lot of code]

However, monomorphization (https://en.wikipedia.org/wiki/Monomorphism) increases binary size, which is considered as its negative aspect. For example, if the Bag struct defined above has a lot of methods which uses a lot of different Ts, this will result in creating a lot of variants. Imagine if we have multiple generic types!

