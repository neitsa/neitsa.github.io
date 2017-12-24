Filtering
=========

Filtering is done by selecting the filters available in the [terrain](terrain.md) and [temperature](temperature.md) tab.

Once you have selected one or more filter, you can click the `Filter` button at the bottom of the main `PrepareLanding` window. The filtered tiles (according to the set of applied filters) are then highlighted on the world map.

There are four categories of filters in `PrepareLanding`:
- [Single choice](#single-choice) filters
- [Three state](#three-states) filters
- [Orderable three state](#orderable-three-state) filters
- [Usable numeric](#usable-numeric) filters

For an example of the three states filters see the [examples](#three-states-filtering-examples):
- [Three States: Simple example](#three-states-advanced-example): A single three state item example.
- [Three States: advanced example 1](#three-states-advanced-example-1): `OR` filtering.
- [Three States: advanced example 2](#three-states-advanced-example-2): `AND` filtering.
- [Three States: advanced example 3](#three-states-advanced-example-3): `AND` filtering + `Partial`.


Single Choice
-------------

The single choice selection is the simplest one: you only have a single choice to select your filter.

For example, the biome selection is one of them as you can only choose one biome at a time.

![biome selection](assets/biomes.png)

# Three States

Three state items have, as their name implies, three possible states:
- On: ![ON state](assets/on_state.png)
- Off: ![OFF state](assets/off_state.png)
- Partial: ![Partial state](assets/partial_state.png)

The `On` state means:
- I absolutely **want** this option when filtering tiles
  
The `Off` state means:
- I absolutely **do not want** this option when filtering tiles
  
The `Partial` state means:
- I **do not care** if this option is available or not when filtering tiles.
  
Note that when clicking on a state item, the order of appearance is: `Partial` -> `Off` -> `On` -> `Partial` -> etc.

# Three States Boolean

Three States Boolean filtering is like the default Three States (standard) filtering except a strict Ternary Boolean filtering takes place.

As of now, only `Roads` and `Rivers` filters support this option.

- `On` state: Boolean `True`
- `Off` state: Boolean `False` (same as a Boolean `NOT`)
- `Partial` state (depends on the type of filter)
    - `OR`: logically same as `On`
    - `AND`: add a supplementary Boolean `OR` check.
    
For examples about the Boolean logic used in these filters please see the [examples](#three-states-filtering-examples).

## Understanding Three States Boolean Filtering

There are two possible Boolean filters:

- `OR`: each of the items are evaluated separately, in conjugation with their state.
- `AND`: all of the items are evaluated together, in conjugation with their state.

### OR Filtering

The `OR` filtering applies a Boolean `OR` operator for each item in the list, where each item describes what should or shouldn't be in the tile.

Think of it as each item being evaluated separately. If any (one or more) of the checks results in a boolean `True` condition, then the tile is included.

*Tip*: Only **one** `True` condition is enough for the tile to be included.

### AND Filtering

The `AND` filtering applies a Boolean `AND` operator for all items in the list, where each item describes what should or shouldn't be in the tile.

Think of it as if all items were evaluated together. If any (one or more) of the checks results in a boolean `False` condition, then the tile is not included.

*Tip*: Put in another way, **all conditions** must be `True` for the tile to be included in the matching list.

### Side Effects

The side effect of a strict boolean filtering is that `False` conditions **never** select anything as the result is discarded.

So if you have to remember one crucial thing when using these filters: `Off` never selects anything!

As an example of this side effect, if you sets all of the roads to `Off` (meaning you don't want any road in the tile) this won't select tiles without any roads...

As this might be counterintuitive a special condition has been implemented so users don't feel the filters are not working correctly: 
If all items are in a `Off` then they still select tiles (in the previous example, this would still select tiles without any road).


Orderable Three States
----------------------

The orderable three state filter works like the [three state filter](#three-states) except the order itself can be changed.

Here is a live example:

![re-orderable three state filter](assets/stone_reordering_optimized.gif)

Note that the reordering is only meaningful for the `On` and `Partial` states (the `Off` state, by definition, has no precise order).

The above example means:
- Filter tiles that have `Sandstone` in first position
- Filter tiles that have `Limestone` in second position
- Filter tiles that may or may not have `Slate` in third position
- Do not include tiles that have `granite`
- Do not include tiles that have `marble`

As of now, only the `Stone type` filter is re-orderable. Please note that for the stone filter, the ordered filtering can be disabled. 


Usable Numeric
--------------

A `usable numeric` filter is comprised of three items:
- A on / off button for the filter usage
    - if `on` the filter is taken into account
    - if `off` the filter is not included
- Two numeric fields (int or float) with a min and max value.

Note: integer fields don't let you enter the decimal point while float fields allow you to do so.

![usable numeric filter: example](assets/select_elevation.png)

Do not forget to click on the `Use` button if you want to use the filter!

![usable numeric filter: use](assets/usable_numeric.gif)


Live Filtering
--------------

Instead of having to click on the `Filter` button, you also have the possibility to use `Live Filtering` by choosing this option in the `Options` tab of the main window.
Be wary that this option may result in CPU heavy combination of filters in some cases, which might result in the game freezing for some time.


Three States Filtering Examples
-------------------------------

## Three states: simple example

Let's take an example with the [Coastal Tile](terrain_tab.md#coastal-tiles) filter on the [Terrain Tab](terrain.md). (`World Map (RimWorld Version: B18); Seed: flo; World coverage: 5%`)

1. Set a [biome filter](terrain_tab.md#biome-type) for `Boreal Forest`.
2. Let the [coastal filter](terrain_tab.md#coastal-tiles) in its default `Partial` state ![Partial state](assets/partial_state.png).

![coastal filter](assets/select_coastal.png)

Now press the `Filter` button at the bottom of the `PrepareLanding` window.

### Partial State

Below is a picture of the highlighted tiles:

![Costal Tiles: partial state](assets/exemple_three_state1_1.png)

As you can see all tiles of the boreal forest biome are highlighted, as the coastal filter is in the `Partial` state. In this state it means: we don't care if tiles are coastal or not.

Put in another way, when a filter is in partial state, it simply means that it both match `On` and `Off`.

### Off State

Now go to the coastal filter and make sure it is in the `Off` state (red checkmark: ![OFF state](assets/off_state.png)). In this state it means: **coastal tiles must not be included**.

Notice how in this state, coastal tiles were removed from the filtering.

![Costal Tiles: Off state](assets/exemple_three_state1_2.png)


### On State

Now go to the coastal filter and make sure it is in the `On` state (green checkmark: ![ON state](assets/on_state.png)) where it means: **only coastal tiles must be included**.

The coastal tile state is `On`, which means: in this state (as we are in the `On` state) only coastal tiles match.

Notice how only tiles that are coastal tiles are highlighted!

![Costal Tiles: On state](assets/exemple_three_state1_3.png)


## Three States: advanced example 1

Roads and Rivers are a combination of multiple three states items (`On`, `Off` and `Partial`) and Boolean filtering.

Here is an example of the [Road Types](terrain.md#road-types) filter on the [Terrain Tab](terrain.md). (`World Map (Rimworld Version: B18); Seed: goldfish; World coverage: 100%`)

The following base filters are applied:

- Biome: Desert
- World Feature (named location): Gatasnaro Plateau

We start our example around tile ID 511159 (5.77°N 172.20°W).

![road filter example: location](assets/exemple_three_state2_1.png)

The following road filters are applied:

- Dirth Path: `On`
- Ancien Asphalt Highway: `On`
- All other roads set to `Off`
- Boolean filter set to `OR`

![road filter: example 1 state 1](assets/exemple_three_state2_2.png)

Here are the resulting filtered tiles:

![road filter: example 1 resulting tiles](assets/exemple_three_state2_3.png)

Now, remember that in Boolean `OR` filtering, each of the items (road types in our case) is applied separately. Thus, the above road filtering means:
- Tile must have a `Ancien Asphalt Highway`
- Tile must have a `Dirt Path`
- I do not want tiles with other types of roads.

In our case this match tiles that have `Ancien Asphalt Highway` or `Dirt Path` or both of them!

Let's proceed with the boolean `AND` filter, with the exact same conditions:

![road filter: example 1 state 2](assets/exemple_three_state2_4.png)

And here is the result:

![road filter: example 1 resulting tiles](assets/exemple_three_state2_5.png)

As you can see this time, it only matches tiles that have both `Ancien Asphalt Highway` and `Dirt Path` **at the same time**, and not the other tiles!

## Three States: advanced example 2

This example demonstrates the Boolean ternary logic applied in the case of the Boolean `AND` filtering when a `Partial` item is included (remember that the `Partial` state has no special meaning in the case of the `OR` filtering).

Given the same location and base filtering as the previous example, let's try first a simple filter:

![road filter: example 2 state 1](assets/exemple_three_state3_1.png)

In this case this means we only want tiles with `Ancien Asphalt Highway` roads (the fact that it is `AND` or `OR` doesn't matter here as they would give the same result).

![road filter: example 2 resulting tiles](assets/exemple_three_state3_2.png)

Now let's add a `Partial` item for `Stone road` with the Boolean `AND` filter selected:

![road filter: example 2 new filter](assets/exemple_three_state3_3.png)

And here's the result:

![road filter: example 2 resulting tiles](assets/exemple_three_state3_4.png)

In this case this means:

- I want roads that have `Ancien Asphalt Highway` (`On` state)
- The matched tiles **may** (due to the `Partial` State) also have a `Stone Road`

In case you aren't sure, here is how would looks the result if we toggled the Boolean filter to `OR` instead of `AND`:

![road filter: example 2 resulting tiles](assets/exemple_three_state3_5.png)

 
As you can see, it independently selects roads that have `Ancien Asphalt Highway` or `Stone Road` or both of them.