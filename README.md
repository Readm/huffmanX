# huffman-X
Huffman code generator supporting various variants of Huffman algorithm.

The purpose of traditional Huffman coding is to minimize the total length after coding, that is, the sum of the product of the frequency `pi` of each coding and its coding length `li` is the lowest. But if our price is not simple length `li`, but other functions, such as the square of length `li ^ 2`, or the power of length `n ^ li`. We need some variants of the basic Huffman function. This module provides this construction method, you can use any quasilinear weight combination functions. Details can be found in the paper.

From paper:

Parker, Jr D S. Conditions for optimality of the Huffman algorithm[J]. SIAM Journal on Computing, 1980, 9(3): 470-489.

Simple induction in Chinese can be found here:

[Huffman树的推广](http://readm.tech/2020/02/03/huffman/)