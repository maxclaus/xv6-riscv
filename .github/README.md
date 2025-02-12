# xv6 RISC-V Kernel

This is a fork of [mit-pdos/xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
with the goal of following the [xv6, a simple Unix-like teaching operating
system](https://pdos.csail.mit.edu/6.828/2024/xv6.html) course.

Xv6 is a teaching operating system developed in the summer of 2006, which we
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
-   [Weekly kernel dev gardening](https://www.youtube.com/watch?v=Jl_8XbTEfSQ)

## Development

Install dependencies:

1. Install [homebrew-riscv](https://github.com/riscv-software-src/homebrew-riscv) (it will provide `riscv64-unknown-elf-gcc` tool to build our kernel targeting RISC-V processor).
2. `brew install qemu` (it will be used to run our kernel on a emulated RISC-V processor).

Run the kernel:

```
make qemu
```
