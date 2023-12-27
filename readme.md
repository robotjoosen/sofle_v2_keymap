# Aurora Sofle v2's Default Keymap
_This keymap is a copy of the [Sofle default keymap](https://github.com/qmk/qmk_firmware/tree/master/keyboards/sofle/keymaps/default), with some modifications._

A simple default keymap for the Aurora Sofle v2
===============================================

Keymaps in general are quite personal, so it is difficult to come up with a default that will suit every user. We hope this keymap serves as a good starting point for your own - although it should be fairly usable out-of-the-box.

What do all these layers do?
----------------------------

### Layer 0: Base layer

![Layer 0](docs/layer_0.png)

### Layer 1: Numpad and Adjustment

![Layer 1](docs/layer_1.png)

### Layer 2: Dev Char and Navigation 

![Layer 2](docs/layer_2.png)

### Layer 3: Hotkeys

![Layer 3](docs/layer_3.png)

Where is the keymap.c?
----------------------

The keymap.c file is not published to the repository. It is generated from `keymap.json` by the build system.

This avoids duplicating information and allow users to edit their keymap from the QMK Configurator web interface.

How do I edit and update the keymap?
------------------------------------

The `keymap.json` file is generated from the QMK Configurator interface and formatted for better readability in the context of the Ferris keyboard.

To edit it, you may:
* Edit it directly from a text editor.
* Edit it from the QMK Configurator.

If you decide to use the latter workflow, here are the steps to follow:

* From the [QMK Configurator](https://config.qmk.fm/#/splitkb/aurora/sofle/rev1/LAYOUT), hit the "import QMK keymap json file" button (it has a drawing with an up arrow on it).
* Browse to the location of your keymap (for example, `<your qmk repo>/keyboards/splitkb/aurora/sofle_v2/keymaps/default/keymap.json`)
* Perform any modification to the keymap in the web UI
* Export the keymap to your downloads folder, by hitting the "Export QMK keymap json file" button (it has a drawing with a down arrow on it)
* Replace your original keymap with the one you just downloaded

_**Note:** At the time of writing (the 24th of October 2022), not every feature used in the default keymap is supported by the QMK Configurator. You cannot yet upload the default `keymap.json` due to a file format mismatch - use the "Load Default" button to load the default keymap instead. Additionally, custom configuration options are still being worked on: if your keymap depends on them, please compile your firmware offline for now._

I want to do more than the JSON format supports!
-------------------------------------------------

While the `json` format is easy to use, it does lack certain functionality - most notably custom OLED or encoder behaviour.

To add this, you need to convert it to the `c` format. Do keep in mind that this is generally a one-way operation.

First, from the root of your qmk repo, move to your keymap folder

```bash
cd ./keyboards/splitkb/aurora/sofle_v2/keymaps/my_personal_keymap
```

Next, convert your `keymap.json` to a `keymap.c`

```bash
qmk json2c -o keymap.c keymap.json
```

You can add custom C code to the newly generated `keymap.c` file. Do note that you have to use **either** a C file **or** a JSON file - you cannot do both!  
**If a JSON file is present, the C file is ignored.**
