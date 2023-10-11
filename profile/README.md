This README is just a fast quick start document.

## What is Florescence


## Install Kernel/compiler/qemu
Nothing specail, install as normal. Only need to install our versions.

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
| 0 | getpid | getpid syscall |
| 1 | context swtich | By using pipe, process A write pipe and process B read pipe. Only have meanings when only two processes are scheduling. |
