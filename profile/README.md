This README is just a fast quick start document.

## What is Florescence


## Install Kernel/compiler/qemu
Nothing specail, install as normal. Only need to install our versions.
### Note
Disable this configs:
```kconfig
CONFIG_X86_5LEVEL=n
```

## Depolyment

## Run tests
1. First clone tests repository in VM.
```git
git clone https://github.com/Florescence-OS/tests.git
```
2. Run tests by using make command
```make
make micro
make normal-micro
```
3. Pass make parameters for control
### micro and macro tests
* process_num: the number of tests processes for both micro and macro tests

### micro tests paramters
* micro_test_idx: the test case used for a single micro test, the detailed tests information is in table below.

| test index | test name | descrption |
|------------|-----------|-------------|
| 0 | context swtich | By using pipe, process A write pipe and process B read pipe. Only have meanings when only two processes are scheduling. |
| 1 | getpid | getpid syscall |
| 2 | small_write | write syscall for PAGE_SIZE chunk |
| 3 | small_read | read syscall for PAGE_SIZE chunk |
| 4 | small_mmap | file mmap syscall for PAGE_SIZE chunk |
| 5 | small_munmap | file unmap syscall for PAGE_SIZE chunk |
| 6 | small_pgfault | first mmap PAGE_SIZE chunk and then access to trigger pagefault |
| 7-11 | mid_* | similar to 2-6, only changes chunk size to 10*PAGE_SIZE |
| 12-16 | big_* | similar to 2-6, only changes chunk size to 1000*PAGE_SIZE |
| 17-21 | huge_* | similar to 2-6, only changes chunk size to 10000*PAGE_SIZE |
| 22 | small_fork | fork with 0 mmap chunck |
| 22 | big_fork | fork with 6000*PAGE_SIZE mmap chunck |
| 22 | huge_fork | fork with 12000*PAGE_SIZE mmap chunck |
| 23 | thread_fork | use pthread() to fork thread |

Note: when you want to test context switch, pls use commands below:
```make
make normal-micro micro_test_idx=0
make micro micro_test_idx=0
```
