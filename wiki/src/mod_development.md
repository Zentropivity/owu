# Mod development

[API documentation can be found here.](https://zentropivity.github.io/owu/api/owu/)

## About bevy

You have to make sure to include bevy features you use in your `Cargo.toml` since game is built with bevy's `default-features` set to `false`.  
[They are documented here for main branch of bevy](https://github.com/bevyengine/bevy/blob/main/docs/cargo_features.md)

TODO what about linux/windows for mods' dependencies? -> some key in `Cargo.toml` to signal if your mod needs OS feature defined.
