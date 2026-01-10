# Types of Command Lists

DirectX 12 defines several types of command lists, each for a specific purpose:

-   **Direct**: The most common type, used for all rendering and compute commands.
-   **Bundle**: A specialized, reusable list for small, repeated command sequences. See [[Bundle]].
-   **Compute**: For `Dispatch` and other compute-specific commands.
-   **Copy**: For resource copy operations like `CopyResource`.

---
*See also: [[D3D12_COMMAND_LIST_TYPE]]*
