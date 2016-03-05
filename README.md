# c-xorshift

Implementation of the Xorshift PRNG algorithm in C


## Usage

The alrogithm takes four unsigned integers as parameters:

```bash
$ gcc -o xorshift xorshift128.c
$ ./xorshift 4094795843 75119171 1064088777 3185678737
3297453526
```


## Implementation

```c
// Marsaglia, George (July 2003). "Xorshift RNGs". Journal of Statistical Software 8 (14).
uint32_t x, y, z, w;

uint32_t xorshift128(void) {
    uint32_t t = x;
    t ^= t << 11;
    t ^= t >> 8;
    x = y; y = z; z = w;
    w ^= w >> 19;
    w ^= t;
    return w;
}
```
