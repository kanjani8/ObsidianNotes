
## Overview
 C and C++ don't have garbage collection and make the programmer manually  manage the memory, which can make high-performance app, but also high chance to have security vulnerabilities.
## Garbage Collection (GC)
- **Role in Memory Management:** GC automates memory allocation and deallocation, simplifying the developer's job.
- **Languages Using GC:** C#, Java, Python, JavaScript, go, ... lots of languages after C++
- **Trade-offs:** Though GC makes coding easier, it can impact performance due to ==pauses== that disrupt program execution.

## Performance Concerns
- **Discord's Decision:** is Switching from Go to Rust,  because of Go's GC-induced performance issues.
- **High-Performance Contexts:** In areas like financial trading, games, and mission-critical software, GC pauses are deemed unacceptable.

## Manual Memory Management
- **C and C++ Requirements:** These languages require developers to manage memory manually, optimizing performance but risking security.
- **Security Vulnerabilities:** 70% of all security vulnerabilities stem from memory safety issues, with common examples including buffer overflow and use-after-free.

## Memory Safety Issues
- **Buffer Overflow:** Described as overfilling a glass, leading to data corruption adjacent memory areas.
- **Use-After-Free:** Accessing memory that has already been freed, causing unpredictable behavior or exploitation.

## The Need for Responsibility
- **Developer's Role:** C and C++ demand a high level of skill to avoid security pitfalls.

## Alternatives and Solutions
- **Memory-Safe Languages:** Suggests using languages like ==Ada and Rust== that minimize risks while requiring manual memory management.
- **Rust's Approach:** Uses a compiler-enforced ownership system to eliminate memory safety issues.

## Long-Term Transition
- **Adoption of Rust:** Despite the challenges of moving away from C and C++, Rust is being integrated into significant projects, including ==the Linux kernel and core Windows libraries.==


[Reference](https://www.youtube.com/watch?v=wFRr-RNhyG0) #NomadCoder