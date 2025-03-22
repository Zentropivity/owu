# World representation

I decided not to go with a regular block grid (voxels) for terrain. Instead, I want something like a low-poly terrain.

Still trying to decide if a planet world would be worth it...

- For planet:
  - Planets are nice and spherical, you can go around in a loop!
  - You can watch the sunset(s) and know that someone else may see it as a sunrise.
  - Flat is boring. Planet is more fun.
  - You could have multiple planets! Probably needs different levels:
    - Galactic scale
    - Each planet with own chunk coordinates
    - Complicated collision detection? Its just voxel with voxel on large scale.
- Against planet:
  - Gravity would not line up with the chunk coordinates, possibly making things difficult to reason about...
    - Some planetary coordinate system could help with that (like irl maps), conversion between them could be implemented
  - Flat is boring.

## Chunks

Space will instead be sliced into equally sized blocks in 3 dimensions, chunks. (Not voxels really...) These chunks can nicely be generated and streamed to players.

- TODO figure out a nice representation for chunks
  - they will need to be networked
  - they will need to be saved to filesystem
  - how big?
    - at least planet Earth size should fit in the game world

## Materials

Terrain has different materials, which impacts the physics simulation. Besides terrain, other, more dynamic entities may be present, each with specific physical materials.

## Multi-server

The idea is simple: let servers own a set of chunks. Make them communicate to handle travelling between them seamlessly.

- An interesting implication: you could have different servers in countries connecting the game world based on in-game position. So travelling to some place would mean going to a server far from you. Thinkers _could_ interact with foreigners but most of the time they would probably stay on their closest server (in their region on the map) for network performance. It would be best to make this completely optional without missing out on the fun.
  - Maybe even make the world a planet with real-time day-night cycle so it would be in sync with your time zone wherever you are.
- Another extension is to start a server and migrate data (and players) based on some heuristics when some region gets overloaded.
