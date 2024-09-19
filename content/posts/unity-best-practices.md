---
title: Unity Engine Best Practices
date: 2024-07-03
draft: true
---

#### Generic Tips
1. **Test your code**
    - Developing a QA process early is key to a maintanable codebase
    - The longer you take to do it = bigger codebase = harder to integrate tests
    - Yes QA costs more short term, but it pays off long term
    - Unity has a decent testing library, go learn how to use it
2. **OOP bad**
    - Unity Engine is designed around OOP paradigms
        - you don't have a choice whether to choose OOP or not (unless using DOTS)
        - however you can still minimize OOP use in your project's codebase
    - Performance in games is critical
        - gamers want their games running at 60+ FPS
        - battery life on mobile is another crucial factor
    - Some OOP "good practices" are considered "bad practices" in gamedev
    - OOP causes memory fragmentation, which causes much higher cache miss rate
    - Prefer having data laid out to minimize cache miss
        - use structs instead of classes where possible
        - also make sure to use *ref* to avoid copying struct data aroud
        - use indices instead of pointers/references
    - Keep abstractions to a low
        - use polymorphic functions instead virtual methods
        - use enums and switchs instead of polymorphism
        - virtual methods in core loops will kill performance due to vtable lookups
    - Prefer composition over inheritance
        - keeps you sane and codebase maintanable
    - Core features of C# can cause GC
        - reference by interface causes boxing/unboxing
3. **Memory allocations, GC, and pooling**
    - C#/.Net has a garbage collector
        - gives you NO way of manually deallocating memory
    - Core features can cause GC
    - Lists can cause GC
        - boxing/unboxing structs
    - Arrays can cause GC
        - can't deallocate arrays
    - Interfaces can cause GC
        - through boxing/unboxing
    - Get used to pooling objects
        - only way to avoid GC
4. **Learn about Unity DOTS**
    - Probably the best thing Unity came up with in many years
    - Job System
        - async multi-threaded job execution
    - Burst compiler
        - compiles C# to near native performance
    - Collections
        - GC-free array allocation API
    - Mathematics
        - shader-like syntax library
        - a godsend gift
    - Unity Physics
        - new mega fast physics engine
    - ...

#### Code Performance Tips
1. **Cache your calls**
    - **.transform** isn't a field, it is a C# property
        - it produces an extern call to Unity's binaries
        - it can be expensive if doing it every frame
    - calling **.transform** does a extern call
    - calling **.gameObject** does a extern call
    - cache values instead