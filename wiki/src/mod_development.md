# Mod development

[API documentation can be found here.](https://zentropivity.github.io/owu/api/owu/)

## Cargo.toml

We use the rust crate `Cargo.toml` file for mod metadata.

```toml
[package]
# you can name it anything, but it would be easier to find them on crates.io if you published them with an `owu_mod_` prefix
name = "owu_mod_fun"
description = "Mod adding many fun things to owu."
version = "0.1.0"
edition = "2024"

# extra config
[owu]
# if your mod works differently (and uses different dependencies) based on os, set this to true and add features like below
os_features = true
load_after = ["owu_mod_other"] # these don't necessarily have to be dependencies

[features]
default = ["os_linux"]
os_windows = ["owu_mod_other/microsoft"]
# note that you can have optional dependencies and dependency features like usual
os_linux = ["owu_mod_other/gigahard", "owu_mod_other_other_other", "bevy/wayland"]
os_mac = ["owu_mod_other/peach"] # I cannot test this os...
ow_web = [] # not sure how to make web work yet... probably could compile to wasm, no mod selection in browser

# use other mods like any crate dependency
[dependencies]
owu_mod_other = "*"
owu_mod_other_other = { git = "https://example.git/owu_mod_oo", rev = "af1234fdc", version = "1.0" }
# path dependencies are discouraged unless they are actually published on crates.io (don't forget version then)
owu_mod_other_other_other = { path = "../owu_mod_ooo", version = "...", optional = true }
# some bevy dependencies are needed unless other dependencies re-export it (for Plugin), you may even use git if you want to track main but make sure to notify thinkers (maybe in readme?)
bevy = "*"
# can also specify bevy sub-crates if you like
bevy_ecs = "*"
```

## Plugin

A public `OwuMod` bevy `Plugin` must be added at crate root, this will be your mod's entry point. Code generation will make sure to add your plugin after other mods you specify in `owu.load_after` in `Cargo.toml`.

If you maintain multiple versions (for like bevy main and last release, or other mods' versions...), you are encouraged to make a dependency table in readme.

## About bevy

You have to make sure to include bevy features you use in your `Cargo.toml` since game is built with bevy's `default-features` set to `false`.  
[They are documented here for main branch of bevy](https://github.com/bevyengine/bevy/blob/main/docs/cargo_features.md)
