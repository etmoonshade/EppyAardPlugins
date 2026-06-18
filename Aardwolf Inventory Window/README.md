# Epsilon's Inventory Monitor

*Vibe coded with Claude, but doesn't suck.*

A live inventory display for [Aardwolf](https://www.aardwolf.com/) on MUSHclient. It shows
your carried inventory, per-container monitors, your keyring, and your vault in
miniwindows — with item flags and decay-timer countdowns — kept up to date from the game's
`invmon` event stream rather than by polling, so it won't add input lag in combat.

## Installation

Copy `Epsilon_Inventory_Monitor.xml` into your MUSHclient `worlds/plugins/` directory and
add it through the Plugins dialog, then type `emon help` in-game for the command list.

## Commands

### `emon`
Toggle all inventory windows.

### `emon monitor <container> [names]`
Tracks a carried container in its own window.

- **`<container>`** matches the *name* of a container you carry, e.g. `bag` or
  `'bag of aardwolf'`. Accepts quotes for multiple words; first match wins.
  *(Note: it does **not** accept `2.'foo bar'` syntax at this time.)*
- **`[names]`** is a comma-separated *name list* matched against displayed item names
  (**not** the keyword). For example:

  ```
  emon monitor 'Bag of Aardwolf' duff, Cobra Blood
  ```

  This shows bag items whose name contains "duff" or "Cobra Blood" in the monitored
  window. Quotes around the item names to monitor are unnecessary, even when multi-word.

Color codes and case are ignored when matching, so it works whether or not you copy with
colors.

### `emon unmonitor <container>`
Closes a monitor window. (You can also click the **!** in the top-left corner of a window
to close it.)

### `emon keyring`
Toggle a window showing your keyring contents.

### `emon vault`
Toggle a window showing your vault contents. Returns the stock error from `vault list` if
you don't have one.

### `emon sort [inv|type]`
Choose between displaying windows in inventory order or grouped by item type. Type order
is like the `invsort type` command. Applies to all windows.

### `emon flags`
Toggles display of item flags on/off.

### `emon shortflags`
Toggles short `(G)` vs long `(Glow)` flags, similar to the `shortflags` command.

### `emon timer [red yellow]`
Items with a timer (i.e. keys) show the amount of time left. By default, items with less
than 24 hours left show in **red**, 24 to 168 hours (1 to 7 days) in **yellow**, and more
than 168 hours in **green**.

The two thresholds can be set as desired, using `d`/`h`/`m`/`s` to specify days, hours,
minutes, or seconds. A number with no identifier assumes hours. For example:

```
emon timer 10m 168
```

The above sets the lower threshold to 10 minutes and the upper to 168 hours (7 days).

Using `emon timer` with no arguments shows the current thresholds.

### `emon stacktimer [soonest|latest]`
When several of one item stack, items show their timer and color based on the **soonest**
item to expire by default. This switches it to base the timer and color on the **latest**
item in the stack instead. With no argument, it toggles.

### `emon tickrate [seconds]`
How often the item countdown display redraws (default 1s). If things feel laggy with a lot
of keys, set this higher to redraw less often.

### `emon refresh`
Resyncs all inventory from the game. Use this if something's acting weird.

### `emon invmon`
Re-enables the `invmon` tags. This should happen on startup, but it's a reminder if it
doesn't. Also, if you uninstall, you'll need to enter `invmon` to turn the tags off.

### right-click a window → Change Font
Like other miniwindows, the font can be changed. Things look fine with a monospaced font.
You're on your own if you insist on a proportional font — it'll look weird.

### `emon help`
This helpfile. Consider yourself PKed.
