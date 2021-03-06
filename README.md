# AES for Lua

1. This files contain an implementation of AES in lua.

2. The only additional library needed is **bitlib**.

3. It can be used to communicat with other platforms or languages.**(such as c, php, lua, java, golang, c#, python)**

4. It can be also used on embedded linux system.**(such as openwrt)**


**Thanks to bighil !**

1. This library is baseed on his project.
 [bighil/aeslua](https://github.com/bighil/aeslua/blob/master/src/aeslua.lua)

2. I fork this project because the origin project created by bighil seems to be no longer updated.



## Usage

```lua
require("aeslua");

cipher = aeslua.encrypt("password", "secret");

plain = aeslua.decrypt("password", cipher);
```

- For further examples,look into the file src/testcryptotest.lua.
- To use AES directly, have a look at aes.lua and at the example usage in testaes.lua.

## Installation

Edit the LIBDIR variable in the Makefile and run
```bash
make install
```

## Speed

> The implementation is rather optimized (it uses tables for most AES operations) 
but still cannot compete with AES written in other languages. Typical AES 
implementations reach several 100 MBit per second, this implementation only 
reaches 400 kBit per second. The most plausible reason is the heavy reliance
of AES on bit operations. As lua numbers are doubles bitlib needs to convert
them to long values for each bit operation.

> So if you need to encrypt much data with AES, do yourself a favor and use a 
C-Implementation. But if you only need to encrypt short strings and you have 
no control over the lua environment (like in games :-)) use this library.

