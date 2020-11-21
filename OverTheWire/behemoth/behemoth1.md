# Behemoth 1

First we run it to see the behavior

```
behemoth0@behemoth:/behemoth$ ./behemoth0
Password: foobar
Access denied..
```

So it expects an input. Let's see if `ltrace` can help reveal what it expects the password to be

```
behemoth0@behemoth:/behemoth$ ltrace ./behemoth0
__libc_start_main(0x80485b1, 1, 0xffffd784, 0x8048680 <unfinished ...>
printf("Password: ")                                                                                                                               = 10
__isoc99_scanf(0x804874c, 0xffffd68b, 0xf7fc5000, 13Password: foobar
)                                                                                              = 1
strlen("OK^GSYBEX^Y")                                                                                                                              = 11
strcmp("foobar", "eatmyshorts")                                                                                                                    = 1
puts("Access denied.."Access denied..
)                                                                                                                            = 16
+++ exited (status 0) +++
```

We can see from this `strcmp("foobar", "eatmyshorts")` that it's comparing the input to the string `eatmyshorts`.

Let's try this as the password

```
behemoth0@behemoth:/behemoth$ ./behemoth0
Password: eatmyshorts
Access granted..
$ whoami
behemoth1
$ cat /etc/behemoth_pass/behemoth1
aesebootiv
```
