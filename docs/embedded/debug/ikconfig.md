# IKCONFIG (Internal Kernel Configuration)

IKCONFIG allows storing the kernel configuration within the kernel image itself. This configuration includes the various options and parameters used during the kernel compilation process. IKCONFIG enables users to inspect the kernel configuration without needing access to the original configuration file used during compilation.

## Configuration

### Kernel configuration

```bash
General Setup  --->
    <*/M> Kernel .config support
        [*] Enable access to .config through /proc/config.gz
```

```bash
CONFIG_IKCONFIG=y
CONFIG_IKCONFIG_PROC=y
```

## How to use

### Reading IKCONFIG

If IKCONFIG support has been built as a module, the module will need loaded into the kernel before use:

```bash
modprobe configs
```

/proc/config.gz is a compressed copy of the kernel configuration, which means that in order to read it, it needs to be decompressed. To parse the content use one of the following:

```bash
zgrep IKCONFIG /proc/config.gz
```

or

```bash
zcat /proc/config.gz > running.config
```

or

```bash
cat /proc/config.gz | gunzip > running.config
```

## References & Notes

https://blog.fpmurphy.com/2015/10/what-is-procconfig-gz.html
https://wiki.gentoo.org/wiki/Kernel/IKCONFIG_support