# Linux System Monitor (C Language)

A real-time terminal dashboard built entirely in **C** using the ncurses library. It displays CPU usage and load average, RAM and swap usage, root filesystem capacity, network throughput, and running processes.

## Features
- CPU utilization and recent usage history
- 1, 5 and 15 minute load averages
- RAM, available memory and swap usage
- Root filesystem capacity
- Network download and upload rates
- Running process list with PID, user, CPU%, memory and command
- Sort processes by CPU (`c`), memory (`m`) or PID (`p`)
- Scroll the process list with Up/Down or `j`/`k`
- Quit with `q`; refreshes approximately every second

## Project structure

```text
monitor/
├── src/
│   └── main.c       # C implementation and ncurses interface
├── Makefile         # GCC build configuration
└── README.md
```

## Requirements
- Linux
- GCC compiler
- ncurses development package

On Debian/Ubuntu:

```bash
sudo apt update
sudo apt install build-essential libncurses-dev
```

## Build and run

```bash
make
./sysmon
```

Or run `make run`. To remove the compiled executable, use `make clean`.

## Language confirmation
The implementation uses C (`.c` source file), standard C/POSIX/Linux interfaces, GCC (`CC`), and ncurses. It does not require C++ or a C++ compiler.

## Data sources
- CPU: `/proc/stat`, `/proc/loadavg`
- Memory: `/proc/meminfo`
- Network: `/proc/net/dev`
- Process information: `/proc/[pid]/stat`, `/proc/[pid]/status`, `/proc/[pid]/cmdline`
- Disk capacity: `statvfs()` on `/`
- Host uptime: `sysinfo()`
