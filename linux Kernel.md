
A unix kernel is typically a monolitic static binary 
that is, it exists as a single large executable image that runs in a single address space.
Unix systems typically require a system with a paged memory-management unit **MMU**
this hardware enables the system to enforce memory protection and to provide a unique virtual address space to each process . linux historically has required an MMU, but special versions can actually run without one. This is a neat feature, enabling Linux to run on very small special versions can actually run without one . this is a neat feature , enabling linux to run on