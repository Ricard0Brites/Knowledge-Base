The objective in this directory is to scan `Quick Notes/**/*.md`, read all the files, rewrite them clearly and to the point, and then insert them into their proper locations in the `Polished Docs` section.

### Updating Existing Notes
If a note in `Quick Notes` has a corresponding note in `Polished Docs`, but the quick note contains additional information, the polished note should be edited to add the missing information in a clean, organised, and pretty manner.

### File and Directory Structure
The vault follows a specific structure:
-   A main folder is named after the content (e.g., `C++`).
-   Inside the main folder, there should be a `Subpages` folder, or a subfolder named after the concept it's going to contain.
-   A file named the same as the parent folder (e.g., `C++.md`) contains the links to the subpages.
-   If there is a subfolder, it should point to the main file inside that folder.

### Formatting
-   The files should be atomized and should contain `[[wiki-style]]` links.
-   Any file that contains more than one header should make use of the `automatic-table-of-contents` plugin by inserting:
    ```table-of-contents
    ```
-   To use the `Fast Text Color` plugin, color text sections using the following syntax: `~={id} This text is colored according to the id=~`. The `id` maps to one of the color formats provided by the current active theme.

### Plugins
We are using Obsidian with the following plugins:
-   auto split
-   automatic table of contents
-   dataview
-   fast text color
-   waypoint

#### Waypoint Plugin Usage
The Waypoint plugin automatically generates tables of contents/MOCs within folder notes.
%% Error: Cannot create a waypoint in the root folder of your vault. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
%% Error: Cannot create a landmark in the root folder of your vault. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
-   **Persistence**: Waypoints are generated and saved as real markdown text.
-   **Important**: Do not remove the `%% Begin Waypoint %%` or `%% End Waypoint %%` flags as these are used by the plugin to locate the table of contents. Any changes made to the text between these flags will be overwritten when the waypoint is updated.
-   **Folder Notes**: Waypoints can only be created within a folder note. It is recommended to use a plugin like `Folder Note` to ensure folder notes don't get lost after renames.

#### Dataview Plugin Usage
The Dataview plugin allows treating your Obsidian Vault as a database that can be queried.
-   **Data Sources**: Information is pulled from Markdown frontmatter (YAML at the top of a document) and Inline fields (e.g., `Key:: Value`).
-   **Query Modes**:
    -   **Dataview Query Language (DQL)**: A pipeline-based, SQL-like language for basic queries.
        Example:
        ```dataview
        table time-played, length, rating
        from "games"
        sort rating desc
        ```
    -   **DataviewJS**: A high-powered JavaScript API for complex queries with full access to the Dataview index.
        Example:
        ```dataviewjs
        dv.taskList(dv.pages().file.tasks.where(t => !t.completed));
        ```
    -   **Inline Expressions**: DQL expressions embedded directly in markdown (e.g., `= this.file.name`).
    -   **Inline JS Expressions**: JavaScript equivalent for inline execution (e.g., `$= dv.current().file.mtime`).
-   **Security Note for JavaScript Queries**: These run with the same access level as other Obsidian plugins and can potentially modify, create, or delete files, or make network calls. Use with caution from trusted sources.
