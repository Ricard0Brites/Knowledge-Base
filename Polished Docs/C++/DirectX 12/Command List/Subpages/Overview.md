# Command List Overview

A **Command List** in DirectX 12 is a sequence of commands recorded by the CPU that the GPU can execute. This explicit control over work submission is a core feature of the API, designed to reduce CPU overhead and enable efficient multithreading.

Command lists are created from a [[Command Allocator]], which manages the underlying memory for the commands.
