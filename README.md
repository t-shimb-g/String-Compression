# String Compression
## Overview
This is an algorithm that uses Huffman codes to encode plaintext into a compressed binary sequence.

## Features
- Compresses user-provided plaintext using Huffman Codes
- Illustrates each step taken in compression process through terminal
- Calculates compression percentage
- Able to decompress file by tracing Huffman tree

## Example
Below is an example of the terminal output: 
```text
Please enter a message:
This is the message that is going to get compressed.

Frequency Table:
d: 1
r: 1
p: 1
T: 1
 : 9
a: 2
n: 1
.: 1
h: 3
i: 4
s: 7
t: 5
g: 4
e: 6
m: 2
o: 3
c: 1

Priority Queue:
(d, 1) -> (p, 1) -> (n, 1) -> (c, 1) -> (r, 1) -> (T, 1) -> (., 1) -> (m, 2) -> (a, 2) -> (o, 3) -> (h, 3) -> (i, 4) ->
(g, 4) -> (t, 5) -> (e, 6) -> (s, 7) -> ( , 9) -> nullptr

Huffman encoding tree:
               (a, 2)
             /
           (cna, 4)
             \
                   (n, 1)
                 /
               (cn, 2)
                 \
                   (c, 1)
         /
       (tcna, 9)
         \
           (t, 5)
     /
   (hm.etcna, 21)
     \
           (e, 6)
         /
       (hm.e, 12)
         \
                   (., 1)
                 /
               (m., 3)
                 \
                   (m, 2)
             /
           (hm., 6)
             \
               (h, 3)
 /
( iTrpdgoshm.etcna, 52)
 \
           (s, 7)
         /
       (gos, 14)
         \
               (o, 3)
             /
           (go, 7)
             \
               (g, 4)
     /
   ( iTrpdgos, 31)
     \
                       (d, 1)
                     /
                   (pd, 2)
                     \
                       (p, 1)
                 /
               (Trpd, 4)
                 \
                       (r, 1)
                     /
                   (Tr, 2)
                     \
                       (T, 1)
             /
           (iTrpd, 8)
             \
               (i, 4)
         /
       ( iTrpd, 17)
         \
           ( , 9)

Huffman codes:
a: 1111
n: 11101
c: 11100
t: 110
 : 000
T: 001100
i: 0010
r: 001101
e: 101
p: 001110
d: 001111
g: 0100
o: 0101
s: 011
.: 10011
h: 1000
m: 10010

Uncompressed bit sequence:
010101000110100001101001011100110010000001101001011100110010000001110100011010000110010100100000011011010110010101110011
011100110110000101100111011001010010000001110100011010000110000101110100001000000110100101110011001000000110011101101111
011010010110111001100111001000000111010001101111001000000110011101100101011101000010000001100011011011110110110101110000
01110010011001010111001101110011011001010110010000101110

Encoded:
001100100000100110000010011000110100010100010010101011011111101001010001101000111111000000100110000100010100101110101000
00110010100001001011100001110001011001000111000110110101101110100111110011

Decoded:
This is the message that is going to get compressed.

Compressed to 46.6346% of original size
```

### TODO:
- **File Compression**:
    - Read a text file, compress its contents using Huffman coding, and save the compressed data to a new file
    - Store the custom Huffman tree in the compressed file to enable decoding
- **File Decompression**:
    - Read the compressed file, reconstruct the Huffman tree, and restore the original text
- **Code Refactoring**:
    - Organize `compress_functions.cpp` into separate classes for better modularity
      - Create a `HuffmanTree` class to handle tree construction, encoding, and decoding
    - Consider a `FileHandler` class to manage reading and writing files