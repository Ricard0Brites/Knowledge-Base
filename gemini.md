# Directory Overview

This directory is a personal knowledge base, structured as an [Obsidian](https://obsidian.md/) vault. It contains a collection of atomic, well-structured notes on various technical topics, primarily focused on software development and computer graphics.

Following a recent refactoring, the vault adheres to a consistent, hierarchical structure to ensure clarity and ease of navigation.

## Directory Structure

The organizational principle is based on nested topics. Each topic or sub-topic has its own directory containing an entry-point Markdown file that links to more granular notes.

The standard structure is as follows:

-   `Topic/`: The top-level folder for a subject (e.g., `C++`, `Design`).
-   `Topic/Topic.md`: The main entry-point file for the subject. This file should contain a `waypoint` to automatically generate a list of sub-topics.
-   `Topic/Subtopic/`: A folder for a sub-topic.
-   `Topic/Subtopic/Subtopic.md`: The main file for the sub-topic. This file should also contain a `waypoint`.
-   `Topic/Subtopic/Subpages/`: A folder containing the atomized notes for the sub-topic.
-   `Topic/Subtopic/Subpages/*.md`: The atomized notes, broken down into individual files for each specific concept.

This system allows for deep, recursive organization of information and promotes the creation of atomic notes.

## Updating Existing Notes
If a note in `Quick Notes` has a corresponding note in `Polished Docs`, but the quick note contains additional information, the polished note should be edited to add the missing information in a clean, organised, and pretty manner.

# Formatting
-   If you want to add "---" at the start of the document you **must** add an enter (breakline) first even if it's an empty line.
-   The files should be atomized and should contain `[[wiki-style]]` references when mentioning other documents.
-   Any file that contains more than one header should make use of the `automatic-table-of-contents` plugin by inserting:
    ```table-of-contents
    ```
-   To use the `Fast Text Color` plugin, color text sections using the following syntax: `~={id} This text is colored according to the id=~`. The `id` maps to one of the color formats provided by the current active theme.
-   Use text coloring where you define as fitting.

# Plugins
We are using Obsidian with the following plugins:
-   auto split
-   automatic table of contents
-   dataview
-   fast text color
-   waypoint

## Waypoint Plugin Usage
- Use this plugin in every `Topic/Topic.md` or subtopic root file. The root file is defined as the file thats named exactly like the folder it is in... eg: `Topic` folder would contain `Topic.md`.
The Waypoint plugin automatically generates tables of contents/MOCs within folder notes.
%% Error: Cannot create a waypoint in the root folder of your vault. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
%% Error: Cannot create a landmark in the root folder of your vault. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
-   **Persistence**: Waypoints are generated and saved as real markdown text.
-   **Important**: Do not remove the `%% Begin Waypoint %%` or `%% End Waypoint %%` flags as these are used by the plugin to locate the table of contents. Any changes made to the text between these flags will be overwritten when the waypoint is updated.
-   **Folder Notes**: Waypoints can only be created within a folder note. It is recommended to use a plugin like `Folder Note` to ensure folder notes don't get lost after renames.

## Dataview Plugin Usage
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

# Version Control
-   If you detect a Version Control System in a project, do not attempt to run any commands with it. This is strictly out of bounds for you unless explicitly instructed otherwise.
-   If you are explicitly instructed to run a VCS command, you are limited to only run the instructed command. This permission is not persistent, and you are not allowed to use VCS commands thereon after.


# Objective
-    The objective is to rewrite, revise, and/or restructure the files inside `Quick Notes` then move these modified files into `Polished Docs` to the correct directory (dependent on use case. you will have to analyse the document being moved and reason where to insert it logically keeping in mind the wanted structure)
-    You also have to keep in mind that if there is missing information you should add it.
-    Any information should be concise, to-the-point, and as short as possible while not sacrificing readability nor the amount of information present in said document;