First, create a character (`c`) device file for our new one-byte device. Read-write permissions are set for all (`--mode 0666`), and the major device driver is the one defined in our driver code (`61`).

```sh
dough@ubdg:~$ sudo mknod --mode 0666 /dev/one c 61 0
dough@ubdg:~$ ll /dev/one
crw-rw-rw- 1 root root 61, 0 Mar 31 22:05 /dev/one
```
