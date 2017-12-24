Terrain 2 & Temperature
=======================

This tabs is split in two parts: the leftmost part is dedicated to terrain filters while the right part is dedicated to temperature related filters.

![Terrain and Temperature Tab](assets/temperature_tab.png)

The [terrain filters](#terrain-filters) are as follows:

* [Most / Least Characteristics](#most-least-feature)
    * Elevation
    * Temperature
    * Rainfall
* [Special Features](#special-features)
    - Caves
* [World Features](#world-features)
    - Named locations
* [The coordinates window](#coordinates-window)

The list of available [temperature related filters](#temperature-filters) in this tab is as follows:

* [Temperatures](#temperatures)
    * Average Temperature
    * Winter Temperature
    * Summer Temperature
* [Growing Period](#growing-period)
* [Rainfall](#rainfall)
* [Animals Can graze Now](#animals-can-graze-now)

The "[Temperature Forecast](#temperature-forecast)" is **not** a filter: it allows you to see the temperature forecasts for a given date at a given tile.

Terrain Filters
---------------

## Most Least Characteristics

This filter allows you to filter different tile characteristics by their most or least prevalence.

![Most Least Characteristics selection](assets/select_most_least.png)

The currently selectable characteristics are:
* Elevation
* Rainfall
* Temperature

Simply put it allows you to select a given number of tiles with the lowest or highest characteristic. For example, you might want to choose the 25 tiles with the highest elevation, or filtering the 100 tiles that have the lowest temperature.

Of course you can combine this filter with other filters.

First you need to select the given feature (elevation, temperature or rainfall) and next the type of the feature (most / least or if you wish highest / lowest).

![Most Least Characteristics](assets/select_most_least_characteristic.png)

![Most Least Characteristics](assets/select_most_least_characteristic_type.png)

To disable the filter, simply choose "None" as the feature to filter. This disable the filter altogether.

## Special Features

As of B18, RimWorld has only one special feature which is "caves".

This filter allows you to filter tiles with caves.

The coastal tile filter is a single [three-state filter](filtering.md#orderable-three-states).

![Caves filter](assets/select_caves.png)

- `On`: Filter only tiles that contain caves
- `Off`: Filter tiles that do **not** contain caves
- `Partial`: both "have caves" and "do not have caves" tiles match (default behavior)

## World Features

This filter let you select tiles in a specific named location (called "World Feature" by the RimWorld code) on the world map.

Below is an example with seed `doctor` on a 5% world:

![World Feature](assets/select_world_feature.png)

By default the `Any` filter means that all names match (and thus the entire world).

Note: be wary that some tiles that are part of a named location might be located quite "far" from the name on the world map.

## Coordinates Window

The coordinates window can be called while the world map is displayed, either by pressing the button in this tab or by pressing `CTRL + M` (`command` for Mac users).

It's a handy way to go to a tile by its ID or its coordinates. The window also displays 4 buttons related to specific locations on the world.

![World Feature](assets/coordinates_window.png)


Temperature Filters
-------------------

## Temperatures

Allows to filter tiles by their temperatures (in °C). These filters are of [Usable Numeric filter](filtering.md#usable-numeric) type.

![Temperatures selection](assets/select_temperatures.png)

The Average temperature can be used to filter tiles by their average temperature (the average temperature of the tile during the whole year).
The other two filters are convenience filters for the summer and winter seasons temperatures.
  
Technically, the game allows temperatures in the range [-270, 1000] °C.

Do not forget to click on the `Use filter` (by default a red cross) if you want the filter to be taken into account.


## Growing Period

Allows to filter tiles by the length of their growing period (in days).

![Growing period selection](assets/select_growing_period.png) 

To use this filter you must first enable it by clicking on the red cross (which then changes to a green check mark) and then use the two buttons.

The first button indicates the minimum growing period to filter and the second button gives the maximum growing period (both are inclusive). 

If you want to search for a single growing period, set the minimum and maximum to the same value.

Obviously, the minimum growing period cannot be greater than the maximum.

Note that since B18 the game gives the growing period as what looks like a fraction:

![Growing Preiod](assets/growing_period.png) 

In this case it means that the growing period is 30 days (out of 60 days which is a RimWorld year) and this growing period goes from the 6th of Aprimay to the 6th of Septober.

Please also note that:

1. The game has a 60 days-long year, so the minimum is `Never` (0 day; no growing period) and the maximum is `Year-round` (60 days).
2. Growing periods are organized in period of 5 days; 5 days = a single Twelfth (as there are 12 twelves in a year, which amounts to a total of 60 days).


## Rainfall

Allows to filter tiles by the quantity of rain / precipitation (in millimeters). Note: Rainfall is useful for farming.

![Rainfall selection](assets/select_rainfall.png) 

This filters is of [Usable Numeric filter](filtering.md#usable-numeric) type.


## Animals Can Graze Now

**Important Note**: this filter is only available while playing (colonies already settled) and not on the world map while selecting the landing site. This is a vanilla game limitation.

![Animals Can Graze Now selection](assets/select_animals_can_graze_now.png) 
  
This filter allows to filter tiles by checking if animals are able to graze at the time of the check.
See [three states filtering](filtering.md#three-states) on how to proceed with this type of filter.


## Temperature Forecast

The temperature forecast allows you to see the temperature forecast for a given tile.

To use this feature:

1. Select a tile on the world map
2. Select a date on the date selector
3. Push the "View Temperature Forecast" button

The date selector allows you to choose the date for which the forecast should be done, it has three main components:

* Day of the Quadrum [1, 15]
* Quadrum [Aprimay, Jugust, Setptober, Decembary]
* Year [5500, 5550]

![Temperature Forecast Selection](assets/temperature_forecast_selection.png)

Once you have pushed the "View Temperature Forecast", the following window appears:

![Temperature Forecast Window](assets/temperature_forecast_window.png)

* The lefmost table indicates the average outdoor temperatures for each hour of the selected day.
* The middle table indicates the average outdoor temperature for each twelves of the selected year.
* The rightmost table gives the minimum & maximum temperatures for the next year, sarting at the selected date (note: a year in RimWorld is 60 days; day 0 being the currently selected day).

The "Tile Specs" gives you various information about the selected day, the selected tile and temperatures.



