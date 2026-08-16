
A unix kernel is typically a monolitic static binary 
that is, it exists as a single large executable image that runs in a single address space.
Unix systems typically require a system with a paged memory-management unit **MMU**
this hardware enables the system to enforce memory protection and to provide a unique virtual address space to each process . linux historically has required an MMU, but special versions can actually run without one. This is a neat feature, enabling Linux to run on very small special versions can actually run without one . this is a neat feature , enabling linux to run on very small MMU less embedded systems, but otherwise more academic than practical even simple embedded systems nowadays tend to have advanced features such as memory- management unit. 

## Monolithic Kernel Versus Microkernel Designs 

Monolithic kernels are implemented entirely as a single process running in a single address space which means 