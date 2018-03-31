# FTPS4 + Jailbreak Kernel Patches

### Features

- FTPS4
- Decrypt eboot/self and sprx
- Jailbreak
- Sandbox escape
- Debug settings
- Enable UART
- Disable system update messages
- Delete system updates
- Fake self support
- Fake pkg support
- RPC server
- RPC client in C#

I use the standard fake pkg keys, created by flatz.

### General Notes
**Only for 4.55 Jailbroken PlayStation 4 consoles!**

The main jkpatch payload utilizes a port of CTurt's payload sdk (xvortex). This requires an environment variable `PS4SDK` pointing to your SDK. Alternatively, change the [Makefile](payload/Makefile) to have `LIBPS4` point to the ps4-payload-sdk directory on your machine. I could have it referenced from the home directory but meh...
```makefile
# change this to point to your ps4-payload-sdk directory
LIBPS4	:=	/home/John/ps4-payload-sdk/libPS4
```

If you decide to edit the `resolve` code in the kernel payload, make sure you do not mess with...
```c
void resolve(uint64_t kernbase);
```
... as it is called from `crt0.s`. And changing this will produce errors.

See other branches for other kernel support. I will support latest publically exploited firmware on main branch.

### RPC Quickstart

See either [Example.cs](librpc/Example.cs) or look at the [RPC documentation](librpc/jkpatch.pdf).

You can read/write memory, call functions, read/write kernel memory, and even load elfs.

[Here](https://www.youtube.com/watch?v=ieQPY4feBZo) is a cool example of an elf loaded into COD Ghosts (forge mod made by me!) You can download the source code to the forge mod [here](http://www.mediafire.com/file/v2m6513km68vmpd/forge.zip). Have fun!

### Coming Soon
- General code clean up and refactoring
- Hope to make standalone elf for FTPS4

### Credits:
**Creator of JKpatch:**

Twitter: [@cloverleafswag3](https://twitter.com/cloverleafswag3) psxhax: [g991](https://www.psxhax.com/members/g991.473299/)
**golden <3**

**Merge with FTPS4** - [Mistawes](https://github.com/mistawes), [xvortex](https://github.com/xvortex), [Xerpi](https://github.com/xerpi)

Thank you to flatz, idc, zecoxao, hitodama, osdev.org, and anyone else I forgot!
