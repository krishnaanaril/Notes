# Garbage Colleciton in .NET (CLR)
## Overview
- When we create an object, CLR allocates memory from the **managed heap**.
- The garbage collector's **optimizing engine** determines the best time to perform a collection, based upon the allocations being made.  
## Fundamentals
- Garbage collector in CLR acts as a automatic memory manager.
- Garbage collector provides memory saftey by making sure that an object cannot use for itself the memory allocated for another object.
- Fundamentals of memory
    - Each process has its own virtual address space. 
    - All process on the same computer share same physical memory and page file.
    - By default on 32-bit computer, each process has 2 GB user-mode virtual address space
- In 32-bit Windows, the total available virtual address space is 2^32 bytes (4 gigabytes). Usually the lower 2 gigabytes are used for user space, and the upper 2 gigabytes are used for system space.
- Virtual memory can be in 3 states: Free, Reserved and Committed.
- When a virtual memory allocation is request, virtual memory manager has to find a single free block that is large enough to satisfy that allocation request.
- You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.
- Allocating memory from the managed heap is faster than unmanaged memory allocation.
- The garbage collector considers unreachable objects garbage and releases the memory allocated for them.
Memory is compacted only if a collection discovers a significant number of unreachable objects.
- To improve performance, the runtime allocates memory for large objects in a separate heap. 
- However, to avoid moving large objects in memory, this memory is usually not compacted.
- Garbage collection occurs when one of the following conditions is true:
    - The system has low physical memory. 
    - The memory that's used by allocated objects on the managed heap surpasses an acceptable threshold.
    - The **GC.Collect** method is called (Only in unique sitations and testing).
- To reserve memory, the garbage collector calls the Windows **VirtualAlloc** function and releases segments back to the operating system (after clearing them of any objects) by calling the Windows **VirtualFree** function.
- The heap can be considered as the accumulation of two heaps: the large object heap and the small object heap. The large object heap contains objects that are **85,000 bytes** and larger, which are usually arrays. 
- We can configure the threshold size for objects to go on the large object heap.
- To optimize the performance of the garbage collector, the managed heap is divided into three generations, 0, 1, and 2, so it can handle long-lived and short-lived objects separately.
- Objects on the large object heap (which is sometimes referred to as generation 3) are also collected in generation 2.
- Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation.
- In .NET Core and in .NET Framework 4.5.1 and later, you can use the GCSettings.LargeObjectHeapCompactionMode property to compact the large object heap on demand.
- It is possible for a base class to only reference managed objects, and implement the dispose pattern. In these cases, a finalizer is unnecessary. A finalizer is only required if you directly reference unmanaged resources.
- The `SafeHandle` class provides a finalizer, so you do not have to write one yourself.