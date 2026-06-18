# EppyAardPlugins

A collection of [Aardwolf](https://www.aardwolf.com/) plugins for MUSHclient. "Vibe coded with Claude, but doesn't suck."

No actual guarantees that it doesn't suck, but all the plugins get tested carefully before I release them. I also focus on performance as much as possible, so it shouldn't bog things down. If I ever do anything that touches the DB outside an established function, you can bet I'm testing the hell out of it before releasing it to make sure it doesn't do some silly corruption to it.

If you find an edge case, let me know and I'll chase it down.

Each plugin lives in its own subfolder with its own README. Drop the `.xml` into
your MUSHclient `worlds/plugins/` directory and add it through the Plugins dialog (Ctrl+Alt+P in MUSH).

## Plugins

- **[Epsilon's Inventory Monitor](Aardwolf%20Inventory%20Window/README.md)** — a live
  inventory display: carried inventory, per-container monitors, keyring, and vault in
  miniwindows, with item flags and decay-timer countdowns. Driven by the game's `invmon`
  event stream, so it stays current without polling.

## License

[WTFPL](LICENSE) — do what the fuck you want to.
