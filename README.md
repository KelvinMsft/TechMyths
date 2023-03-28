# TechMyths
This doc intends to explain technical myths which are poorly explained or defined or a industrial terminology which is hard to be searched on Google or Wikipedia, that a myth could be a term, or a concept, even a functionality that provided by any instance, like hardware or OS.

I would treat this doc act as a low level technical dictionary or a research helper to accelerate people who interested in studying low level area, so we can avoid reading thousands irrelevant pages to actually find few lines of useful sentences in different paper or datasheet.

This will not document every single low level concept but for those which is really hard to be searched on the internet.

Contribution is welcome.

- [TechMyths](#techmyths)
  - [Memory-Mapped I/O (MMI0)](#memory-mapped-io-mmi0)
  - [PCI based MMIO Device](#pci-memory-mapped-io-mmi0)
  - [Base Address Register (BAR)](#base-address-register-bar)
  - [Direct Memory Access (DMA)](#direct-memory-access-dma)
  - [ACPI device namespace](#acpi-device-namespace)
  - [UEFI](#uefi)

## Memory-Mapped I/O (MMI0)
MMIO is a method that a software, usually the device drivers, to access the registers in the devices through the memory interface, which is the ability that provided by the address decoder, after memory mapped unit translates the virtual address into physical address, it forwards the request to Local APIC, I/O APIC, southbridge or PCH, or any other devices according to the hardware specific system memory map, depends on the implementation.

## PCI based MMIO device
MMIO is the functionality that provided by the hardware itself, however, unlike local APIC, I/O APIC, etc... There's a lot of devices are not defined in the system memory map during manufacturing, these devices could possibly be a PCI-compliant, all the PCI-compliants could "dynamically" extend the system memory map through its machanism.

Upon the PCI Root Complex/ Host Bridge receive the decoded address, it generates the transaction and fills the physial memory address onto AD[0..31] or AD[0..63] lines, and each devices got 3 cycle to respond the transaction according to its Base Address Register (BAR), and that is positve decoded. Otherwise, if there's no devices on the bus are positvely respond (decode) to the request, the host would just forward the request to those device which would like to unconditionally claim the request for further dispatch, it is subtractively decoded, another bus device like PCI-to-PCI bridges, then creates another transaction within its topology, and so on.

## Base Address Register (BAR)
BAR are usually allocated within a dedicated memory range based on the SoC series where we called it as PCI Memory Address Range, and the corresponding UEFI/BIOS is generally accountable for the address assignment for each PCI device, we also call that device memory.

## Direct Memory Access (DMA)
DMA is a way that device read and write the main memory.

## ACPI device namespace
OSes usually convert ACPI namespace into device tree, and find the corresponding drivers to load, if the devices itself are bus device like USB controller or PCI-to-PCI bridge, they will trigger another round of device enumeration and load the corresponding drivers, such as, input devices.

## UEFI
It is a unified interface for BIOS developer.

