# A Kernel Seedling

This is a kernel module designed for Arch Linux that generates a process at `/proc/count`. When you type `cat /proc/count`, it prints the number of processes. To get the number, the module looks at the kernel's process table. This is a basic way to see some of what the kernel is doing.

## Building
```shell
make
sudo insmod proc_count.ko
```

The C code is compiled into a kernel object file with the '.ko' extension. This kernel module is then loaded into the running Linux kernel. This will generate some output files, one of which should be `proc_count.ko`. 

## Running
```shell
cat /proc/count
```

The expected output for this command is an integer indicating the current number of running processes in the `/proc/count` module. While testing, my result was 148.

## Cleaning Up
```shell
sudo rmmod proc_count
make clean
```

`sudo rmmod proc_count` removes the kernel module, while `make clean` cleans up build artifacts.

## Testing
```python
python -m unittest
```

Testing resulted in 3 tests being run in 8.684s, all passing successfully.

Report which kernel release version you tested your module on
(hint: use `uname`, check for options with `man uname`).
It should match release numbers as seen on https://www.kernel.org/.

```shell
uname -r -s -v
```

This command spits out the kernel version: `Linux 5.14.8-arch1-1 #1 SMP PREEMPT Sun, 26 Sep 2021 19:36:15 +0000`