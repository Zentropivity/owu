# What is owu?

It intends to be an easily moddable multiplayer sandbox game that I can work on in my spare time.  
As such the core game will probably be written by me but I am open to new ideas and requests. I also plan to sell a launcher for it on Steam for the not-so-technomancers and people who want to support the endeavor.

- Open world sandbox 
- [Open source](https://github.com/Zentropivity/owu)
  - core game mostly made by: `Zentropivity <zen@zentropivity.eu>`
- Efficient -> [made in Rust](https://doc.rust-lang.org/stable/book/)
  - uses the [bevy game engine](https://bevyengine.org/)
- Moddable: using bevy plugins you can change most of the game  
  I strive to make the documentation as useful as possible. Do not hesitate to [read rustdoc](https://zentropivity.github.io/owu/api/owu/) and please [let me know](https://matrix.to/#/#owu_modding:zentropivity.eu) if its bad somewhere.
- Futuristic fantasy
  - the world is home to magic and wonders, with the Humans extinct what will happen to their creations and the world?
- Skills skills skills: you will know what you will know  
  (or more if you read the source code, do what you want.)

## Where is owu?

- [Zentropivity/owu repository](https://github.com/Zentropivity/owu)
- [API docs - rustdoc](https://zentropivity.github.io/owu/api/owu/)
- [Wiki - developer notes](https://zentropivity.github.io/owu/wiki/)
- Matrix:
  - [\#owu:zentropivity.eu](https://matrix.to/#/#owu:zentropivity.eu) (space that fails to list its rooms...)
  - [\#owu_discussion:zentropivity.eu](https://matrix.to/#/#owu_discussion:zentropivity.eu)
  - [\#owu_modding:zentropivity.eu](https://matrix.to/#/#owu_modding:zentropivity.eu)
- TODO: publish my launcher on steam.

## Motivation

I wanted to make a moddable game and I like to do things the hard way if it means efficiency will be born or it sates my curiosity.  
Rust is my favorite language to read and write code in but there are several issues when it comes to modding...

- Data only goes so far, so we need some kind of code mods for sure, but...  
  Writing a scripting api is another layer I don't really want to deal with. Scripts definitely don't run as fast as equivalent rust code either and I like high performance applications.  
  Shared libraries then?..
- People don't really add dylib to potential package types on popular libraries so its kind of painful to work around diamond linking issues...
  - It seems there are no real ABI stability guarantees unless you use `extern "C"` in cdylib which is *yek*.  
    (I read it somewhere (maybe in the rust book or nomicon) that even between rustc calls, one struct may generate different code... which would mean that passing structs into other rust dylib's functions may not work even on same rust version when not compiled together.)
- And how would a mod developer use another mod's types and functions? Something like documentation and a C header would need to be publicized.

So for all of it to work I sacrifice some kind of ownership of the code and require the same from mod devs too.  
(The launcher, I will monetize but the actual game will be open source and reproducing one version of the executable game is straightforward.)

The idea is simple:

- Open source the game, in several packages.
- Make the launcher compile the game on the player's machine.
- Let the player manage mods using repositories and possibly changing the source code locally.

This should result in...

- An open game that is easy to mod.
- Mods that are easy to interface with.
- Some people learning to code to play a game slightly differently. xD
- High transparency. Players can normally look inside the mod's source code too.

## But what does owu mean?

Something like:

- Open World Universe
- OwO With UwU
- Ocean Waits Under
- Ordinary Wet Underwear
- Orbs Want Unknown
- Oh What U?!
- Oily Wind Underestimated
- Obvious War Underground
- Old Weary Upperbody
- Or Word Understanding

Or whatever you can think of... Let me know if you think of more good interpretations.
