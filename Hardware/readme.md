# Memory
## RAM (Random Access Memory)
### Capacity

Higher GB is better
RAM sizes follow powers of 2 because computers operate in binary and memory addressing works as 2^n.

### Generation

SD>DDR>DDR2>DDR3>DDR4>DDR5
Each generation is faster and more efficient, but your motherboard must support it.

### Speed
Higher MHz → faster data transfer.

### Channels

How many memory pathways the system uses.
Single channel → slower
Dual channel → faster (most common)
Quad channel → used in high-end systems

### Latency:
Lower latency = faster response.

## ROM (Read only Memory)
### SSDs
- 2.5-inch SATA SSD
- M.2 SSD (SATA & NVMe)
- mSATA SSD
- External/Portable SSD
  
| Feature | 2.5" SATA SSD | M.2 SATA SSD | M.2 NVMe SSD (Gen 4/5) |
| :--- | :--- | :--- | :--- |
| **Physical Form** | 2.5-inch Drive (Boxy) | M.2 Stick (Gum stick) | M.2 Stick (Gum stick) |
| **Interface** | SATA III | SATA III | PCIe (NVMe Protocol) |
| **Max Data Speed** | ~560 MB/s | ~560 MB/s | 7,000 to 10,000+ MB/s |
| **Connection** | SATA & Power Cables | Motherboard Slot | Motherboard Slot |
| **Best Use Case** | Budget/Mass Storage | Older Thin Laptops | OS Boot / Gaming / Video Editing |
| **Relative Cost** | Lowest | Medium | Higher |

#### RAID
RAID 0 (Striping): **Splits data across at least two hard disks** to make **read and write speeds faster**, but offers no backup if a drive breaks.

RAID 1 (Mirroring): Copies the exact **same data onto two hard disks** so that if one drive fails, your data is still safe on the other.

RAID 5 (Distributed Parity): Uses **three or more hard disks to spread data and safety codes (parity)** so the system keeps working even if one drive breaks, **Parity is used to rebuild the data** in the event of a failure.

RAID 5,10 both needs to have **4 disks minimum**

RAID 10: both side is striped using RAID 0, It used fault tolerance of RAID 1, and speed of RAID 0. Downside: **you can only use the 50% capacity** of your disk space.

#### M.2 SATA vs NVMe
##### Interface

- SATA M.2 – Uses the same interface as old SATA SSDs. Max ~550 MB/s.
- NVMe M.2 – Uses PCIe lanes, much faster.
Most modern systems prefer NVMe. Each generation of NVMe provides double speed from previous gen.

##### PCIe Generation (NVMe)
Higher Generation = higher theoretical bandwidth

##### Read/Write Speed
Higher Better

##### NAND Type
The memory inside the SSD matters.
- SLC – fastest, expensive (rare in consumer drives)
- MLC – high endurance
- TLC – common balance of speed + cost
- QLC – cheaper, lower endurance
Most good consumer drives use TLC NAND.

#### Capacity
Higher Better.


# Motherboad

1. ATX (Advanced Technology eXtended)

- Size: 305 × 244 mm
- Most common motherboard size for desktop PCs.
- Offers many PCIe slots, RAM slots, and ports.
- Good for gaming PCs and high-performance builds.

✅ Pros
- Lots of expansion options
- Better cooling space
- Supports multiple GPUs and storage

2. Micro-ATX (mATX)

- Size: 244 × 244 mm
- Smaller version of ATX.
- Fits in both ATX and smaller cases.

✅ Pros

- Cheaper than ATX
- Compact but still decent expansion
- Good for budget or mid-range builds

3. Mini-ITX

- Size: 170 × 170 mm
- Very compact motherboard used for small PCs.

✅ Pros

- Ideal for small form factor (SFF) PCs
- Low power consumption
- Perfect for HTPCs or mini gaming builds

❗ Limitation: Usually only 1 PCIe slot and 2 RAM slots

4. E-ATX (Extended ATX)

- Size: about 305 × 330 mm
- Larger than ATX.

✅ Pros

- More RAM slots and PCIe slots
- Used for workstations and high-end gaming rigs

5. Nano-ITX

- Size: 120 × 120 mm
- Very small motherboard mainly used in embedded systems.

6. Pico-ITX

- Size: 100 × 72 mm
- Extremely small form factor.

Used for:

- IoT devices
- Industrial computers
- Embedded electronics


# PC CASE 
SFX<Mini Tower<Mid Tower<Full Tower
