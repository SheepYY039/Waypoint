# Waypoint - Automatic Table of Contents Generator for [Obsidian.md](https://obsidian.md/)

Do you use folders to categorize your notes and wish that Obsidian would show certain folders in the graph view? Do you hate having to keep track of tags and links every time a file is created? Do you want to decide what folders should be categories without creating index files for every folder?

Waypoint is an Obsidian plugin that automatically generates tables of contents/MOCs within your folder notes. Once a waypoint is generated, it'll automatically link to every note within the folder and its subfolders. The Waypoint plugin will detect when you create/rename/move/delete a note and automatically stay up-to-date. **No more dealing with loads of tags or manually updating your own content maps!**

## Features

- **Automatically generated tables of contents!**
	- Waypoints are created whenever you type the magic word (default is `%% Waypoint %%`) within a folder note. A folder note is any note with the same name as its parent folder.
- **Instant updates whenever files/folders are created, renamed, moved, or deleted**
	- 	File path changes trigger a scan for any waypoints that might be affected. If a waypoint is found, it is instantly updated in real-time.
- **Folders can now appear on the graph view**
	- Just create a waypoint in a note with the same name as the folder and it'll automatically link to every file within, including files in subfolders!
	- Waypoints can be "nested" to avoid unnecessary links
		- Say your folders go from `A -> B -> C`. If you put a waypoint in the folder note of folder A, it'd include every file within folders A, B, and C. But if you create another waypoint in folder B, the first waypoint would only link to that folder note.
- **Fine-grained control over which folders are considered categories**
	- Since you decide when and where a waypoint is generated in your folder tree, you can decide which folders could be considered "categories" and which are just for organizing.
	- Say you have a folder tree like `Latin -> Chapter I -> Vocab -> ...`. "Latin" and "Chapter I" might be considered important enough to be called categories, but the "Vocab" folder within each chapter is just used to keep things organized. Other plugins might require that an index file is made in every folder, but Waypoint allows you to pick and choose what folder notes contain tables of contents. This means you can avoid creating a waypoint in each "Vocab" folder while still having the waypoints in each chapter folder like directly to each term. And because of how Waypoint prioritizes folder hierarchy, the waypoint in the folder note for "Latin" will only link to the chapter folder notes to avoid creating unnecessary links!
- **Permanent and portable**
	- Waypoints are generated and saved as real markdown text within your folder notes unlike other plugins. If you decide to switch to a different markdown editor that supports [[links]], all of your tables of contents will still be usable.
	- Note that the Waypoint plugin currently only works with Obsidian, so moving files around in another editor will cause your waypoints to be out-of-date.

## How To Use

- First, install the plugin. Waypoint is currently being reviewed for inclusion to the Community Plugins list. Once it is accepted, you'll be able to install it directly within Obsidian.
- Generate a waypoint by editing a folder file (a file with the same name as its parent folder) and typing in the waypoint trigger text. By default this is `%% Waypoint %%`. Make sure to include the double-parentheses on both sides!
	- This trigger flag can be changed in settings, but it will always require the double-parentheses as that is how Obsidian knows it's a comment and not real text.
- And that's it! Waypoints will be automatically updated whenever the files or folders within that folder are changed. Be sure not to remove the `%% Begin Waypoint %%` or `%% End Waypoint %%` flags as this is what the plugin uses to locate the table of contents. Any changes made to the text between these flags will get removed once the waypoint is updated.

## Current Limitations

- Waypoints can only be created within a folder note
	- Because scanning for waypoints every time a file/folder is changed is an intensive process, only folder notes are checked to avoid scanning every file in the vault.
- Waypoints cannot be created on the top level of your vault
	- Waypoints are meant to categorize notes that are similar to one another. Adding a waypoint to the root node would cause every note in your vault to be linked and defeat the point of using waypoints in the first place
- Waypoint appearance can't be customized (yet)
- Only notes with the same name as the folder they are in will be considered "folder notes"
- Only one waypoint can be created per folder note

If your workflow would be improved by the removal of one of these limitations, feel free to reach out to me with your use case and I'll see what I can do!

## FAQ

### How is this different from indexing plugins like [Zoottelkeeper](https://github.com/akosbalasko/zoottelkeeper-obsidian-plugin)?

Zoottelkeeper and other related plugins are much more complex and try to solve a different problem. Zoottelkeeper automatically creates index files for every single folder in your repository (with customizable blacklists and whitelists). This means that each folder shows up on the graph view and only links to the index file in the folder immediately below the current one. This is great if you use folder's sparingly and each folder has a significant and specific meaning, but if you use folders as your main method of organization then your graph will quickly become messy.

Waypoint was created to give users fine-grained control over what folders are considered signficant enough to be considered a "category" of notes. It allows you to create tables of content that link not only to the files in the same folder but to files in subfolders as well. And if you decide that certain subfolders are worthy of a subcategory of their own, creating a waypoint there will automatically prune the parent waypoint and update it to link only to that folder's folder note. If you prefer to have your waypoints only link to the nearest folder note (whether or not they contain a waypoint), TODO
