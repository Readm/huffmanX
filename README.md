# huffman-X
Huffman code generator supporting various variants of Huffman algorithm.

The purpose of traditional Huffman coding is to minimize the total length after coding, that is, the sum of the product of the frequency `pi` of each coding and its coding length `li` is the lowest. But if our cost is not simple length `li`, but other functions, such as the square of length `li ^ 2`, or the power of length `n ^ li`. We need some variants of the basic Huffman function. This module provides this construction method, you can use any quasilinear weight combination functions. Details can be found in the paper.

From paper:

Parker, Jr D S. Conditions for optimality of the Huffman algorithm[J]. SIAM Journal on Computing, 1980, 9(3): 470-489.

Simple induction in Chinese can be found here:

[Huffman树的推广](http://readm.tech/2020/02/03/huffman/)

Usage:

Provided an iterable of 2-tuples in (symbol, weight) format, generate a Huffman codebook, returned as a dictionary in {symbol: code, ...} format.

```
>>> codebook([('A', 2), ('B', 4), ('C', 1), ('D', 1)])
{'A': '10', 'B': '0', 'C': '110', 'D': '111'}
If you have an iterable of symbols, the collections.Counter is a handy way to tally them up.

>>> codebook(collections.Counter('man the stand banana man').items())
{'m': '111', 'a': '01', 'n': '10', ' ': '000', 't': '0010', 'h': '1101', 'e': '11000', 's': '11001', 'd': '00110', 'b': '00111'}
```

The default weight combination function is `F(x,y)=x+y', i.e. the traditional Huffman tree.
If you want to change the weight combination function, add a argument called `weight_fun`.

For example:
If `F(x,y)=2x+2y`, the root weight means the total cost if the cost of one symbol is `2 ^ li`. As the result shows, the codings prefer shorter encodings.

```
>>> codebook(collections.Counter('man the stand banana man').items(),weight_fun=lambda x,y: 2*(x+y))
{'m': '101', 'a': '11', 'n': '001', ' ': '010', 't': '0000', 'h': '0001', 'e': '1000', 's': '1001', 'd': '0110', 'b': '0111'}
```
