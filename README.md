# 🌟 LightyOS

![LightyOS](https://img.shields.io/badge/LightyOS-v0.1-blue)
![Status](https://img.shields.io/badge/Status-Experimental-orange)
![Architecture](https://img.shields.io/badge/Architecture-x86--64--targeted-lightgrey)
![Boot](https://img.shields.io/badge/Boot-BIOS%20%2F%20Floppy-informational)

> 🪶 **A lightweight operating system built from the ground up.**

**LightyOS** is a lightweight experimental operating system project focused on learning, low-level development, simplicity, and eventually building a usable Unix-like environment. ⚙️🖥️

The project is currently in **very early development** 🚧. It is intended for experimentation, development, and learning rather than use as a production operating system.

---

# 🚀 What is LightyOS?

LightyOS aims to become a small, understandable operating system built step-by-step from the lowest levels upward.

The basic idea:

```text
BIOS
 ↓
💾 Bootloader
 ↓
📦 Stage 2
 ↓
🧠 Kernel
 ↓
⌨️ Keyboard
 ↓
💻 Shell
 ↓
📦 Package Manager
 ↓
🌐 Networking
 ↓
🗂️ Filesystem
```

The project is intentionally being built in layers instead of dropping a huge amount of code into the system all at once.

---

# 🎯 Project Goals

LightyOS is being designed around a few main goals:

🪶 **Lightweight**
Keep the system small and avoid unnecessary overhead.

🧠 **Understandable**
Build the operating system in a way that makes the low-level components understandable.

⚙️ **Modular**
Add major subsystems incrementally instead of creating one giant monolithic prototype.

💻 **Unix-like**
Eventually provide a familiar command-line environment and Unix-style userspace.

📦 **Real package management**
Eventually support real package metadata and real packages rather than a fake package format.

🌐 **Networking**
Eventually provide networking support so LightyOS can communicate with package repositories and other systems.

🐧 **Linux compatibility goals**
Long-term compatibility with existing Linux software is a goal, but this is **not currently implemented**.

---

# 🛠️ Current Version

## 🟦 LightyOS v0.1 — First Boot

**v0.1** is the first major proof-of-concept release.

The current focus is getting the complete boot chain working:

```text
🔥 BIOS
   ↓
🔥 Bootloader
   ↓
🔥 Stage 2
   ↓
🔥 Kernel
   ↓
🔥 Keyboard
   ↓
🔥 Shell
```

LightyOS currently boots from a raw **1.44 MB floppy image** and enters a basic command-line shell.

---

# ✅ Current Features

## 💾 Boot System

LightyOS currently includes:

* ✅ BIOS bootloader
* ✅ Stage 2 bootloader
* ✅ Kernel loading
* ✅ Kernel memory handoff
* ✅ BIOS text output
* ✅ Raw floppy image generation
* ✅ VirtualBox development/testing
* ✅ Bootable `.img` creation

The current image layout is:

```text
┌─────────────────────────────┐
│ Sector 1                    │
│ 💾 boot.bin                 │
├─────────────────────────────┤
│ Sectors 2-5                 │
│ 📦 stage2.bin               │
├─────────────────────────────┤
│ Sectors 6-13                │
│ 🧠 kernel.bin               │
├─────────────────────────────┤
│ Remaining floppy space      │
│ 💤 Currently unused         │
└─────────────────────────────┘
```

Current image size:

```text
📀 1,474,560 bytes
```

---

# 🧠 Kernel

The current kernel is a small **16-bit real-mode kernel** serving as the foundation for future development.

The kernel currently provides:

* 🖥️ Screen initialization
* ⌨️ Keyboard initialization
* 💬 Basic shell
* 📝 Command buffer
* ⌫ Backspace handling
* 🔤 Character input
* 📺 BIOS text output
* 🔄 Restart support

The default shell prompt is:

```text
lightyos:/#
```

---

# 💻 Shell

LightyOS currently provides a small command-line shell.

## 📋 Available Commands

```text
help
clear
version
echo <text>
restart
```

### Examples

```text
lightyos:/# help
```

```text
lightyos:/# version
```

```text
lightyos:/# echo Hello LightyOS
```

```text
lightyos:/# clear
```

```text
lightyos:/# restart
```

---

# 📦 LPM — LightyOS Package Manager

LightyOS includes an early package manager interface called:

```text
lpm
```

**LPM** stands for:

> 📦 **LightyOS Package Manager**

The current implementation is intentionally tiny and exists as a prototype for the future package-management system.

---

## 🧰 Current LPM Commands

```text
lpm help
lpm list
lpm search <package>
lpm info <package>
lpm update
lpm install <package>
lpm remove <package>
lpm upgrade
```

Example:

```text
lightyos:/# lpm list
```

---

# 📦 Current Prototype Packages

The current built-in catalog contains:

```text
busybox
bash
coreutils
hello
```

These names are currently used for **prototype package-management functionality**.

They do **not** mean LightyOS currently ships these projects or redistributes their binaries.

---

# ⚠️ LPM Status

The current LPM implementation is **not yet a real network package manager**.

At the current stage:

```text
❌ No network repository
❌ No package downloads
❌ No persistent package database
❌ No filesystem-backed installation
❌ No real .deb installation
❌ No real dependency resolver
❌ No package signature verification
```

Instead, the current implementation provides:

```text
✅ Package listing
✅ Package searching
✅ Package information
✅ Prototype install state
✅ Prototype remove state
✅ update command interface
✅ upgrade command interface
```

Install/remove state is currently **volatile** and is stored only while the kernel is running.

---

# 🐧 Future Debian Package Support

One of the long-term goals of LPM is support for **real Debian-style package metadata and `.deb` packages**.

The project does **not** currently claim Debian package compatibility.

Before real package installation can happen, LightyOS needs more infrastructure, including:

```text
🧠 Memory management
🗂️ Filesystem
💾 Persistent storage
🌐 Networking
📡 Network protocols
📦 Package database
🔐 Package verification
🧩 Dependency handling
⚙️ Userspace programs
```

The intended development path is therefore:

```text
Shell
 ↓
Filesystem
 ↓
Storage
 ↓
Memory Management
 ↓
Userspace
 ↓
Networking
 ↓
Package Database
 ↓
LPM Repository Support
 ↓
Real Package Installation
```

---

# 🗺️ Roadmap

## 🟢 v0.1 — First Boot

Current development stage:

* [x] BIOS bootloader
* [x] Stage 2 loader
* [x] Kernel loading
* [x] Kernel entry
* [x] Keyboard initialization
* [x] Basic shell
* [x] Command buffer
* [x] Backspace
* [x] `help`
* [x] `clear`
* [x] `version`
* [x] `echo`
* [x] `restart`
* [x] LPM prototype
* [x] Raw `.img` generation

---

## 🟡 Next Development Stage

Planned work:

* [ ] Direct PS/2 keyboard driver
* [ ] Better keyboard handling
* [ ] Screen/terminal improvements
* [ ] Memory management
* [ ] Basic filesystem
* [ ] Disk/storage abstraction
* [ ] Persistent files
* [ ] Userspace programs
* [ ] Better shell
* [ ] Process management
* [ ] System calls

---

## 🟠 Networking

Planned:

* [ ] Network device detection
* [ ] Network driver support
* [ ] Ethernet support
* [ ] Basic network stack
* [ ] IP networking
* [ ] DNS
* [ ] TCP/UDP support
* [ ] Repository communication

---

## 🔴 Future LPM

Long-term LPM goals:

```text
lpm update
lpm search <package>
lpm info <package>
lpm install <package>
lpm remove <package>
lpm upgrade
```

Eventually:

```text
🌐 Repository
      ↓
📋 Package metadata
      ↓
🔎 Dependency resolution
      ↓
📥 Download
      ↓
🔐 Verify
      ↓
📦 Extract/install
      ↓
🗂️ Update package database
```

---

# 🧪 Development Environment

LightyOS is currently developed on **Windows**.

The development toolchain currently includes:

* 🪟 Windows
* 🛠️ NASM
* 💻 PowerShell
* 🖥️ VirtualBox
* 🔧 x86 assembly

The current project structure is:

```text
LightyOs/
│
├── boot/
│   ├── boot.asm
│   ├── boot.bin
│   ├── stage2.asm
│   └── stage2.bin
│
├── kernel/
│   ├── kernel.asm
│   ├── keyboard.asm
│   └── kernel.bin
│
├── Build-LightyOS.ps1
│
└── LightyOS-v0.1.img
```

---

# 🔨 Building LightyOS

The project includes a PowerShell build script.

Run:

```powershell
powershell -ExecutionPolicy Bypass -File "C:\Users\Amin\Desktop\LightyOs\Build-LightyOS.ps1"
```

The script:

```text
🧹 Cleans old binaries
      ↓
🔧 Assembles bootloader
      ↓
📦 Assembles Stage 2
      ↓
🧠 Assembles kernel
      ↓
💾 Creates floppy image
      ↓
✍️ Writes bootloader
      ↓
✍️ Writes Stage 2
      ↓
✍️ Writes kernel
      ↓
🔎 Verifies image
      ↓
✅ LightyOS-v0.1.img
```

---

# 🖥️ Running in VirtualBox

LightyOS currently targets BIOS-style booting from a floppy image.

Use:

```text
C:\Users\Amin\Desktop\LightyOs\LightyOS-v0.1.img
```

as the VM's floppy disk.

A successful boot should eventually reach:

```text
Initializing keyboard... [ OK ]

lightyos:/#
```

---

# 📜 Project Status

LightyOS is currently:

> 🚧 **Experimental / Early Development**

It should be expected to:

* crash 💥
* freeze 🧊
* contain bugs 🐛
* change architecture 🔧
* break compatibility 🔨
* have incomplete features 🚧

That is normal for the current stage of development.

This repository represents an evolving operating-system project, not a finished product.

---

# ⚖️ Licensing & Third-Party Software

LightyOS source code should be clearly licensed in this repository.

Third-party projects are **not automatically part of LightyOS** simply because LightyOS may eventually aim to support software from those ecosystems.

When third-party software, libraries, source code, binaries, package metadata, or other materials are incorporated into the project:

* 📜 Their applicable licenses must be respected.
* 🧾 Required copyright and license notices should be preserved.
* 📦 Redistribution should only happen when permitted.
* 🔗 Third-party projects should be properly attributed where required.
* 🚫 LightyOS should not claim ownership of third-party software.
* 🚫 LightyOS should not imply endorsement or affiliation that does not exist.

Until real third-party packages are actually integrated, the LPM prototype should not be treated as redistributing those packages.

---

# 🔐 Security

Security is **not yet a major completed subsystem** of LightyOS.

Future security work may include:

* 🔐 Package verification
* 🛡️ Permission systems
* 🔑 User accounts
* 🧾 File permissions
* 🔒 Secure storage
* 🌐 Network security
* 📦 Package integrity checking

Do not use the current experimental builds for sensitive or production workloads.

---

# 🤝 Contributing

LightyOS is an experimental project and contributions may eventually be welcome.

Ideas, bug reports, documentation improvements, testing, and technical discussion can all help the project grow. 🛠️

Before contributing code from another project, make sure its license permits the intended use.

---

# 🐛 Bug Reports

Found a bug?

Please include:

```text
🖥️ Host OS
💻 VM software / hardware
📦 LightyOS version
📝 What happened
🔁 Steps to reproduce
📋 Error output
```

For boot problems, include the **exact text displayed on screen**.

---

# 🌌 Long-Term Vision

The ultimate goal is to evolve LightyOS from a tiny bootable experiment into a lightweight Unix-like operating system.

The long-term vision looks something like:

```text
             🌟 LIGHTYOS
                  │
        ┌─────────┴─────────┐
        │                   │
      🧠 Kernel          💻 Userspace
        │                   │
   ┌────┼────┐         ┌────┼────┐
   │    │    │         │    │    │
  💾   ⌨️   🌐        🐚   📦   🛠️
 Disk Keyboard Net    Shell  LPM  Tools
        │
        ▼
     🗂️ Filesystem
        │
        ▼
     📦 Packages
        │
        ▼
   🌐 Repositories
```

The goal is not to rush toward a huge feature list.

The goal is to understand and build each layer.

**One subsystem at a time.** 🧱⚙️

---

# ❤️ Why LightyOS?

Because making an operating system is fucking cool. 🔥

Starting from:

```text
01010100 01001000 01000101
```

and eventually reaching:

```text
lightyos:/#
```

is the fun part.

LightyOS is an experiment in learning how the pieces of an operating system actually fit together — from booting hardware to kernels, drivers, storage, networking, userspace, and package management.

---

# ⭐ Star the Project

If you're interested in low-level programming, operating systems, kernels, assembly, or just watching this thing slowly become less broken:

**⭐ Star the repository.**

More importantly:

**🔥 Watch it evolve.**

---

# 📌 Disclaimer

LightyOS is an independent experimental project.

It is **not** a Linux distribution, Debian distribution, or official project of Debian, the Linux Foundation, GNU, BusyBox, or any other third-party project unless explicitly stated.

Third-party names mentioned in the documentation may refer to future compatibility goals, package metadata concepts, or examples and do not by themselves indicate inclusion or redistribution.

---

# 🚀 LightyOS v0.1

```text
              ╔════════════════════════════╗
              ║        🌟 LightyOS         ║
              ║          v0.1              ║
              ║                            ║
              ║       First Boot 🚀        ║
              ║                            ║
              ║       lightyos:/#          ║
              ╚════════════════════════════╝
```

**Built from scratch. 🛠️**

**Built to learn. 🧠**

**Built to evolve. 🚀**
