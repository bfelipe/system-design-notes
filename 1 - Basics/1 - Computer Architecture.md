# Computer Architecture

Computer architecture is a set of of hardware components that fits together to make a machine works.
Sofware rely on how these components are proper arrenged in the machine to perform its intended tasks.
A simple overview of how a machine looks inside can be described as:

- Hard Disk
- Memory (RAM)
- CPU
- Cache

There are other components that also has its importance such as:

- GPU
- Network Intefaces

But they are very important this simple study notes.

## Hard Disk

This component is responsible to store your data, in such way that even if your machine shuts down, you can still access its content in late moment.
Hard Drive nowadays can be found in two flavors, HDD and SSD. HDD works in a more mechanical way, where a magnetic disk is writen using sort of a nail.
SDD is a modern Hard Disk and way faster, since it works totaly digitally as a simple chip.
Hard Drivers can be measure in terms of read/write in a time unit called millisseconds (ms).

## Memory (RAM - Random Access Memory)

This component is responsible to load your data from disk, in such way that CPU can be maniputate in late opperations.
Memory doesn't persist data as Hard Drive does. Once your program terminate or your machine is shut down, all data store there will be erased.
Memory can be measured in terms of read/write in a time unit called microsseconds (μs).

## CPU (Central processor unit)

This component is the heart and brain of the machine. It is responsible to access the instructions loaded from memory as binary and execute in such manner to perform
all manner of tasks of your programs.
CPU can perform any sort of operations in the data in your memory and hard disk, such as: sum, subtraction, multiplication, division, aggregation, filtering, etc.

## Cache

This last component is embedded in the CPU. Some data can be often used by the CPU and it is not as large to be stored in memory. In this case, the OS (operational system) will store this data into the CPU cache for quickly use.
Applications can often benefit of this sort of design, such web applications, where data is not often changed and don't need to be request many times over the network.
Cache can be measures in terms of read/write in a time unit called nanosseconds (ns).


## Computer Diagram

![](/images/1.png)