## DebugFS

The debugfs framework in the Linux kernel is a virtual file system designed specifically for debugging purposes. It provides an interface for kernel developers to expose debugging information dynamically at runtime.

## Configuration

### Kernel configuration

```bash
CONFIG_DEBUG_FS=y
```

## How to use the framework

### Mounting debugfs

Debugfs can be mounted much like any other virtual filesystem using the mount command.

Create a mount point. The default is typically /sys/kernel/debug/, which may already exist:

```bash
mkdir -p /sys/kernel/debug
```

Mount the filesystem:

```bash
mount -t debugfs none /sys/kernel/debug
```

## References & Notes

https://lwn.net/Articles/115405/
https://linuxlink.timesys.com/docs/wiki/engineering/HOWTO_Use_debugfs
