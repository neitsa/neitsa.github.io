# Filtering

There are 4 type of filter items in `PrepareLanding`:

- Single choice items
- Three states items
- Reorderable three states items
- Usable numeric fields


## Single Choice


The single choice selection is the simplest one: you only have a single choice to select your filter.

For example the biome sleection is one ofh them as you can only choose one biome at a time.

![biomes selection](assets/biomes.png)

## Three states


Three state items have, as their name implies, three possible state:

- On: ![ON state](assets/on_state.png)
- Off: ![ON state](assets/off_state.png)
- Partial: ![ON state](assets/parial_state.png)

The `On` state means:
    - I absolutely *want* this option when filtering tiles
    
The `Off` state means:
    - I absolutely *do not want* this option when filtering tiles    
    
The `Partial` state means:
    - I do not care if this option is available or not when filtering tiles
    
    
### Three states: simple example

Let's take an example with the [Coastal Tile](terrain.md#coastal-tiles) filter on the [Terrain Tab](terrain.md). (`World Map -> Version: A17b; Seed: flo; World coverage: 5%`)

![coastal filter](assets/select_coastal.png)

Below is an overview of the world map where:

- the Boreal Forest biome is filtered (all Boreal Forest biome tiles are highlighted)
- The coastal tile state is `On`, which means: **coastal tiles must be included**

![Costal Tiles: On state](assets/exemple_three_state1_1.png)

In this state, (as we are in the `On` state) all coastal tiles match. Note that this is the same behavior for the `Partial` state (which would mean: I don't care if it's coastal or not).

Now here is an overview of the world map where:

- The Boreal Forest biome is filtered (all Boreal Forest biome tiles are highlighted)
- The coastal tile state is `Off`: **coastal tiles must not be included**

![Costal Tiles: Off state](assets/exemple_three_state1_2.png)

Notice how in this state, coastal tiles were removed from the filtering.

### Three states: adavanced example

Here is an example with the [Road Types](terrain.md#road-types) filter on the [Terrain Tab](terrain.md). (`World Map -> Version: A17b; Seed: flo; World coverage: 5%`)

![road filter](assets/select_road.png)