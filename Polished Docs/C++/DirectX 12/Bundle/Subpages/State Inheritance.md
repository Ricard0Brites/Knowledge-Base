# Bundle State Inheritance

A bundle inherits most of its state from the parent command list that executes it. However, it does **not** inherit:

-   The [[Pipeline State Object (PSO)]]
-   The primitive topology

Any state changes made within a bundle (e.g., setting a new viewport or scissor rect) will persist in the parent command list after the bundle finishes execution.
