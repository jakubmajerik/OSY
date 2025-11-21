# UNIX System Architecture

graph TB
    A[Hardware] --> B[Kernel]
    B --> C[System Calls]
    C --> D[Shell]
    D --> E[User Space]
    B --> F[Process Management]
    B --> G[Memory Management]
    B --> H[File System]
    B --> I[I/O Operations]
