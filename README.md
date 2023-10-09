
# Godot is disrespecting signal error number in Linux

Run:

> godot4 --headless --export-release "Linux/X11" junk/

Error output:

> Godot Engine v4.1.2.stable.nixpkgs.399c9dc39 - https://godotengine.org
 
WARNING: Custom cursor shape not supported by this display server.
     at: cursor_set_custom_image (servers/display_server.cpp:480)
> ERROR: This project doesn't have an `export_presets.cfg` file at its root.
> Create an export preset from the "Project > Export" dialog and try again.
>   at: _fs_changed (editor/editor_node.cpp:1003)

Then, check for signal error:

> echo $

0

As there are errors in log, it shouldn't be 0 but higher than 0. This causes issues in CI (won't block pipeline) and in Linux operations (won't be understood as failure). This does not comply to expectations for applications.