# xv6 RISC-V Kernel

This is a fork of [mit-pdos/xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
with the goal of following the [xv6, a simple Unix-like teaching operating
system](https://pdos.csail.mit.edu/6.828/2024/xv6.html) course.

Xv6 is a teaching operating system developed in the summer of 2006, which was ported
ported xv6 to RISC-V for a new undergraduate class 6.1810.

## Course

This MIT course content is public and can be used by anyone who want to learn
about design and implementation of operating systems, and their use as a
foundation for systems programming.

The course has a [Schedule](https://pdos.csail.mit.edu/6.1810/2023/schedule.html) page which
can be used as a guideline to follow the course content.

## Resources:

-   [xv6 website](https://pdos.csail.mit.edu/6.828/2024/xv6.html)
-   [xv6 source code](https://github.com/mit-pdos/xv6-riscv)
-   [xv6 book](https://pdos.csail.mit.edu/6.828/2024/xv6/book-riscv-rev4.pdf)

## Videos

-   [xv6 Kernel](https://www.youtube.com/watch?v=fWUJKH0RNFE&list=PLbtzT1TYeoMhTPzyTZboW_j7TPAnjv9XB) - Great series covering xv6 kernel.
-   [Source Dive][source_dive_video]
-   [Weekly kernel dev gardening](https://www.youtube.com/watch?v=Jl_8XbTEfSQ)

## Running

First, install dependencies:

1. Install [homebrew-riscv](https://github.com/riscv-software-src/homebrew-riscv) (it will provide `riscv64-unknown-elf-gcc` tool to build our kernel targeting RISC-V processor).
2. `brew install qemu` (it will be used to run our kernel on a emulated RISC-V processor).

Then, actually run the kernel using qemu emulator with the risc-v processor:

```
make qemu
```

To quit `qemu` type: `Ctrl-a x`.

## Source code

Walk through the code base to have an overview of what each piece is for. This is based on [Source Dive][source_dive_video] video, check that out for more details.

### kernel directory

-   `kernel.ld`: Is a [link script](https://ftp.gnu.org/old-gnu/Manuals/ld-2.9.1/html_chapter/ld_3.html) specifying the entry point for the for kernel.
-   `entry.S`: Just enough assembly code to get the kernel started. It setups the stack for C and calls the `start.c` next.
-   `start.c`: Move from machine mode to supervisor mode, and calls `main.c` to setup the operating system.
-   `param.h`: Configurable parameters used by the system.
-   `main.c`: Setup the operating system, prints the boot message. At this point the kernel is running in supervisor mode already.
-   `riscv.h`: Specific assembly code for RISC-V used by the kernel.

### Glossary

-   `mhartid` (machine mode hart id): is the CPU id, which is used in the kernel boot time
-   `virtual memory`: it works as a container of memory for processes. The OS maps virtual memory to physical memory for processes, so on process cannot access memory from another process.

## Notes

In RISC-V has these modes by level of privilege, being most privilege at top and less privilege at the bottom:

-   Machine mode: it has full access to everything.
-   Supervisor mode: where the operating system runs on.
-   User mode: where program processes run on.

[source_dive_video]: https://www.youtube.com/playlist?list=PLP29wDx6QmW4Mw8mgvP87Zk33LRcKA9bl
