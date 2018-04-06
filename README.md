## /dev/one
#### A read-write device with 1 byte capacity

##### 1. Make node in /dev
First, create a character (`c`) device file for our new one-byte device. Read-write permissions are set for all (`--mode 0666`), and the major device driver is the one defined in our driver code (`61`).

```sh
dough@ubdg:~$ sudo mknod --mode 0666 /dev/one c 61 0
dough@ubdg:~$ ll /dev/one
crw-rw-rw- 1 root root 61, 0 Mar 31 22:05 /dev/one
```

##### 2. Compile as a kernel module
The default target of the Makefile can then be invoked with the one-word command `make`

```sh
$ make
```

##### 3. Install the kernel module
To install the module, from the directory containing the `*.ko` file, execute the command:
```sh
sudo insmod ./one-byte.ko
```

##### 4. Use the one-byte device
To read the byte:

```sh
cat /dev/one
```

To write the byte:

```sh
printf A > /dev/one
```

##### 5. Remove the kernel module
To remove the module:

```sh
sudo rmmod one_byte
```

##### 6. See the driver logs
The printk statements in the module code can be seen in the kernel debug message buffer, by executing `dmesg | tail`.
