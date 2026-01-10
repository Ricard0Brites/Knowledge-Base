# Bundle Overview

A **Bundle** in DirectX 12 is a secondary [[Command List]] optimized for recording a small, reusable sequence of rendering commands. Unlike direct command lists, bundles are designed to be executed multiple times, often within different parent command lists.

The key benefit of bundles is CPU performance. Drivers can pre-process the commands at record time, making subsequent executions extremely cheap. This is ideal for drawing many instances of the same object (e.g., trees, bullets) where the core drawing logic is identical.
