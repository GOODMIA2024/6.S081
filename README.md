# 6.S081

## SP Notes

Each lab has its own branch in the repository. Labs completed so far: 

| Repo Branches                                                | Lab Notes (some WIP)                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [🔗Lab Util](https://github.com/GOODMIA2024/6.S081/tree/util)    |                                                              |
| [🔗Lab Syscall](https://github.com/GOODMIA2024/6.S081/tree/syscall) |                                                              |
| [🔗Lab Page tables](https://github.com/GOODMIA2024/6.S081/tree/pgtbl) | [📒【fin】Lab Notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab3-pgtbl.md) |
| [🔗Lab Traps](https://github.com/GOODMIA2024/6.S081/tree/traps)  | [📒【fin】Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab4-traps.md) |
| [🔗Lab Lazy page allocation](https://github.com/GOODMIA2024/6.S081/tree/lazy) | [📒【fin】Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab5-lazy.md) |
| [🔗Lab Cow](https://github.com/GOODMIA2024/6.S081/tree/cow)      | [📒Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab6-cow.md) |
| [🔗Lab Thread](https://github.com/GOODMIA2024/6.S081/tree/thread) | [📒【fin】Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab7-thread.md) |
| [🔗Lab Lock](https://github.com/GOODMIA2024/6.S081/tree/lock)    | [📒Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab8-lock.md) |
| [🔗Lab File System](https://github.com/GOODMIA2024/6.S081/tree/fs) | [📒【fin】Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab9-fs.md) |
| [🔗Lab Networking](https://github.com/GOODMIA2024/6.S081/tree/net) | [📒【fin】Lab notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab11-net.md) |


## Weekly Roadmap

Prep -> Lec video&slides -> Lab

## Suggested prerequisite

in retrospect, seems that simply taking all the pre-lecture readings seriouly will do (even for os new comers)

## Progress

Completed whitin 3 months (part-time).

- [x] 【0820】init repo && materials && setup
- [x] 【0821】reading1+lec1
- [x] 【0824】lab util
- [x] 【0912】prep2, lec2(slidesOnly)
- [x] 【0915】review concepts+labUtil, lec 3 prep + live
- [x] 【0917】lab syscall
- [x] 【0920+】prep3, lec4+5+6, lab pgtbl
- [x] 【0928】preps, lec 7+8, lab traps
- [x] 【0930】preps, lec 9, lab lazy
- [x] 【1003】prep (ch6 & code), lec 10,
- [x] 【1005】lab cow, prep11, lec 11, lab thread
- [x] 【1011】prep, lab lock
- [x] 【1013】prep fs, lec 14 & lec 15
- [x] 【~1028】prep, lec 16, lab fs
- [x] 【1030】prep, lec 17, 18
- [x] 【1031】lab networking, lec 19, lec 20, FIN!

### W7

Prep

- chap 8
- code

lab fs:

- see notes

### W6

Prep:

- chapter 6&7
- code examples

lab  thread + lock:

- see notes

### W5

Prep:

- chapter 4.6
- code pieces (trap.c, uart.c, plic.c, console.c)

Lab lazy alloc:

- see [lab lazy notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab5-lazy.md)

### W4

Prep:

- riscv calling convention
- lec5&6&7

Lab traps:

- see [lab traps notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab4-traps.md)

### W3

Prep:

- xv6book Chap3
- kernel/memlayout.h, kernel/vm.c, kernel/kalloc.c, kernel/riscv.h, and kernel/exec.c
- Lec 3&4

Lab pgtbl (Page tables):

- see [lab pgtbl notes](https://github.com/GOODMIA2024/6.S081/blob/main/notes/lab3-pgtbl.md)
  

### W2

Prep：

- pointers in K&R C programming
- chap2, 4.3, 4.4 of xv6 book

- syscall和process相关的源码

Lab syscall:

- 一开始想复杂了 实际上实现trace要做的只是：
  - 给每个process打上"标签" ==> 
  - 并把这个标签传递给子进程 ==>  
  - 最后在syscall()时根据标签判断是否需要print trace

- 实现syscall：
  - 【准备】完成各种文件里的函数/变量申明
  - `sysproc.c`中call sysinfo()
  - `sysinfo.c`中，call nproc() 和freemem()，然后用copyout()把sysinfo拷贝到user处
  - `kernel/kalloc.c`中实现freemem() ：统计free memory的大小（利用struc run统计N of free page，可以参考函数kalloc()）
  - `kernel/proc.c`中实现nproc() ：统计进程数量（穷举NPROC并判断struc proc里的state以计数）

### W1

Prep work: Read Chapter 1 of http://xv6.dgs.zone/

Lec:

- [a text overview](https://pdos.csail.mit.edu/6.828/2020/lec/l-overview.txt)
- [example materials](https://pdos.csail.mit.edu/6.828/2020/lec/l-overview/)

Lab Util:

- Useful commands:
  - `make qemu`: xv6 booting
  - `ctrl-a + x`: quit qemu
  - `make clean`: clean production files
  - `ctrl-p`: print information about each process
  - `make grade`: local test for all commands
  - `./grade-lab-util someCommand`or `make GRADEFLAGS=someCommand grade`: runs the local tests for a specific command
- Reminder: dont forger to add command to `UPROGS` in Makefile
- Error fix:
  - [Mac M1] `make grade` reports `env: python: No such file or directory`. Solution: `ln -s $(which python3) /usr/local/bin/python`
  - 对于每个branch，需要在user/sh.c的runcmd函数前添加`__attribute__((noreturn))`，不然xv6启动会报错

## Other Notes

### GBD

About How to use GDB https://zhuanlan.zhihu.com/p/354794701

- `make qemu-gdb`

- in another window && same dir:`riscv64-unknown-elf-gdb`