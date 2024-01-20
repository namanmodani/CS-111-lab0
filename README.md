# A Kernel Seedling

This is a kernel module designed for Arch Linux that generates a process at /proc/count. When you type "cat /proc/count", it prints the number of processes. To get the number, the module looks at the kernel's process table. This is a basic way to see some of what the kernel is doing.

## Building
```shell
make
sudo insmod proc_count.ko
```

## Running
```shell
cat /proc/count
```
TODO: results?

## Cleaning Up
```shell
sudo rmmod proc_count
make clean
```

## Testing
```python
python -m unittest
```
TODO: results?

Report which kernel release version you tested your module on
(hint: use `uname`, check for options with `man uname`).
It should match release numbers as seen on https://www.kernel.org/.

```shell
uname -r -s -v
```
TODO: kernel ver?