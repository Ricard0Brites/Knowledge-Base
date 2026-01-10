# Bundle Restrictions

To achieve this high level of optimization, bundles have several restrictions:

-   They cannot contain commands that change the render target.
-   `Clear` and `Copy` commands are not allowed.
-   Resource barrier commands are forbidden.
-   They cannot be submitted directly to a [[Command Queue]]. They must be executed by a direct command list via `ExecuteBundle`.

These limitations ensure the driver can make strong guarantees about the bundle's behavior, enabling aggressive pre-processing.
