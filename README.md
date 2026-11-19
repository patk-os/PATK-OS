# PATK-OS (PanicAtTheKernel Operating System)

> *"The monolithic era is over. Ring 0 is not a nightclub."*

[![Build Status](https://img.shields.io/badge/status-active%20development-orange.svg)](#)
[![License: BSD-3-Clause](https://img.shields.io/badge/license-BSD--3--Clause-green.svg)](#)
[![Platform: x86_64](https://img.shields.io/badge/platform-x86__64-blue.svg)](#)

**PATK-OS** is a modular, high-reliability, microkernel-based operating system designed from bare-metal up for the 64-bit era. It serves as a modern, crash-proof alternative to the overgrown complexity of Linux and the architectural stagnation of legacy Unix systems.

---

## The Vision

Operating systems were meant to manage hardware, not swallow user space whole. Today's mainstream monolithic kernels ship millions of lines of third-party driver code inside the highest processor privilege tier. 

PATK-OS revives the true spirit of modular Unix design combined with modern microkernel performance:

1. **Failure Is Contained:** Drivers, file systems, and network protocols run entirely in unprivileged user space (Ring 3). A crashing GPU or Wi-Fi driver does not panic the OS—it is transparently reincarnated.
2. **Minimalist by Law:** If it doesn't need to be in the kernel, it isn't. The Ring 0 core remains lean, auditable, and deterministic.
3. **Pure 64-Bit:** No baggage from the 1980s. No real-mode workarounds. Pure, optimized x86_64 execution.

---

## Operating System Structure

PATK-OS is engineered as a collection of decoupled, specialized components:

* **[`patk-kernel`](https://github.com/panicatthekernel/patk-kernel):** The hyper-minimal microkernel (Ring 0). Handles scheduling, memory paging, and high-performance IPC.
* **`patk-servers`:** Essential system servers running in user space:
  * `vfs`: Virtual File System layer.
  * `pm`: Process and memory authorization manager.
  * `rs`: Reincarnation Server (monitors and restarts failed drivers/servers).
* **`patk-drivers`:** Sandboxed user-mode device drivers (PCIe, NVMe, USB, Network).
* **`patk-userland`:** Standard POSIX runtime, libraries, shell, and core utilities derived and adapted from the NetBSD project.

---

## Getting Started

```bash
# Clone the complete OS source tree (WIP)
git clone https://github.com/panicatthekernel/patk-os.git
cd patk-os

# Check out the kernel core
git submodule update --init --recursive
(Build toolchains and deployment scripts are currently under active development.)

# Contributing
We are looking for low-level systems engineers fluent in C, C++, and x86_64 Assembly. If you believe that kernel stability should be guaranteed by hardware architecture rather than corporate promises, you belong here.

# License
PATK-OS and its official subcomponents are distributed under the permissive BSD 3-Clause License.
