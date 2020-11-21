# Narnia 2 (WIP)

```
narnia2@narnia:/narnia$ ./narnia2
Usage: ./narnia2 argument
```

```
narnia2@narnia:/narnia$ ./narnia2 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Segmentation fault
```


https://wiremask.eu/tools/buffer-overflow-pattern-generator/

```
narnia2@narnia:/narnia$ gdb -q narnia2
Reading symbols from narnia2...(no debugging symbols found)...done.
(gdb) run
Starting program: /narnia/narnia2 
Usage: /narnia/narnia2 argument
[Inferior 1 (process 3076) exited with code 01]
(gdb) run Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag
Starting program: /narnia/narnia2 Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag

Program received signal SIGSEGV, Segmentation fault.
0x41346541 in ?? ()
(gdb) q
A debugging session is active.

	Inferior 1 [process 3082] will be killed.

Quit anyway? (y or n) y
```

Then put in this value `0x41346541` which lets us know that the offset is 132.
