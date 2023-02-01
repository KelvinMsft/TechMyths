# TechMyths

- [TechMyths](#techmyths)
  - [Base Address Register (BAR)](#base-address-register-bar)
  - [Memory-Mapped I/O (MMI0)](#memory-mapped-io-mmi0)
  - [Direct Memory Access (DMA)](#direct-memory-access-dma)
  - [ACPI device namespace](#acpi-device-namespace)
  - [UEFI](#uefi)

## Base Address Register (BAR)

BAR are usually allocated within a dedicated memory range based on the SoC series where we called it as PCI Memory Address Range, and the corresponding UEFI/BIOS is generally accountable for the address assignment for each PCI device, we also call that device memory.

## Memory-Mapped I/O (MMI0)
MMIO is a method that a software, usually the device drivers, to access the registers in the PCI-compliant devices through the memory interface, which is the ability that provided by the PCI topology, after memory mapped unit translates the virtual address into physical address, it forwards the transaction to southbridge or PCH, depends on a platform implementation, then fills the physial memory address onto AD[0..31] or AD[0..63] lines, and each devices got 3 cycle to respond the transaction according to its Base Address Register (BAR).

## Direct Memory Access (DMA)
DMA is a way that device read and write the main memory.

## ACPI device namespace
OSes usually convert ACPI namespace into device tree, and find the corresponding drivers to load, if the devices itself are bus device like USB controller or PCI-to-PCI bridge, they will trigger another round of device enumeration and load the corresponding drivers, such as, input devices.

## UEFI
It is a unified interface for BIOS developer.

