---
sidebar_position: 1
---

# Phoenix

A lightweight macOS window and app manager scriptable with JavaScript. You can also easily use languages which compile to JavaScript such as TypeScript. Phoenix aims for efficiency and a very small footprint. If you like the idea of scripting your own window or app management toolkit with JavaScript, Phoenix is probably going to give you the things you want. With Phoenix you can bind keyboard shortcuts and system events, and use these to interact with macOS.

- Current version: 4.0.1 ([Changelog](https://github.com/kasper/phoenix/blob/master/CHANGELOG.md))
- Requires: macOS 10.14 or higher

## Key Features

- highly customisable, write your own configuration
- bind keyboard shortcuts and system events to your callback functions
- control and interact with your screens, spaces, mouse, apps and windows
- log messages, deliver notifications, display content or ask input with modals
- run external commands like you would in the command line

## Example Configuration

Below you will find a basic configuration example. Copy and paste it to `~/.phoenix.js`. When you press the key combination <kbd>Control</kbd> + <kbd>Shift</kbd> + <kbd>Z</kbd> on your keyboard, the focused window will be moved to the centre of your main screen. Happy hacking! 👩🏼‍💻

```javascript
Key.on('z', ['control', 'shift'], () => {
  const screen = Screen.main().flippedVisibleFrame();
  const window = Window.focused();

  if (window) {
    window.setTopLeft({
      x: screen.x + (screen.width / 2) - (window.frame().width / 2),
      y: screen.y + (screen.height / 2) - (window.frame().height / 2)
    });
  }
});
```

Phoenix lives on your status bar (or as a background daemon). Here, Phoenix is being used to move a window to different corners of the screen.

![Screenshot of Phoenix](https://raw.githubusercontent.com/kasper/phoenix/master/assets/screenshot.gif)

## Install

- [**Download Phoenix**](https://github.com/kasper/phoenix/releases/download/4.0.1/phoenix-4.0.1.tar.gz)
- See previous [releases](https://github.com/kasper/phoenix/releases/)

To install, extract the downloaded archive and just drag-and-drop Phoenix to your `Applications` folder. When you run Phoenix for the first time, you will be asked to allow it to control your UI. macOS will ask you to open `Privacy & Security` in System Settings. Once open, go to the `Accessibility` section and enable with the toggle next to Phoenix. An admin account is required to accomplish this.

Alternatively, if you have [Homebrew](https://brew.sh) installed, you can simply run `brew install --cask phoenix`.

## Uninstall

To uninstall Phoenix, delete the app from your `Applications` folder. The configuration file created by Phoenix itself is located in your home folder. Delete `~/.phoenix.js` and any related configurations if desired.

Application preferences are stored in `~/Library/Preferences/org.khirviko.Phoenix.plist`.

If you have used the storage, also delete the file `~/Library/Application Support/Phoenix/storage.json`.

For uninstalling additional support files, see the following folders.

:::info Support Files
```
~/Library/Application Scripts/org.khirviko.Phoenix.Launcher
~/Library/Caches/org.khirviko.Phoenix
~/Library/Containers/org.khirviko.Phoenix.Launcher
~/Library/HTTPStorages/org.khirviko.Phoenix
~/Library/WebKit/org.khirviko.Phoenix
```
:::

## JavaScript API

This documentation is an overview of the JavaScript API provided by Phoenix. Currently, the supported version of JavaScript is based on the ECMAScript 6 standard. macOS versions prior to Sierra (10.12) support ECMAScript 5.1. Use this as a guide for writing your window management script.

Your script should reside in `~/.phoenix.js`. Alternatively — if you prefer — you may also have your script in `~/Library/Application Support/Phoenix/phoenix.js` or `~/.config/phoenix/phoenix.js`.

Phoenix includes [Lodash](https://lodash.com) (4.17.15) — you can use its features in your configuration. Lodash provides useful helpers for handling JavaScript functions and objects. You may also use JavaScript [preprocessing](getting-started/preprocessing) and languages such as TypeScript to write your Phoenix configuration.

## Contact

If you have any questions, feedback or just want to say hi, you can [open an issue](https://github.com/kasper/phoenix/issues/), [start a discussion](https://github.com/kasper/phoenix/discussions/), [email](mailto:kasper@kytkemo.com) or message on [Threads](https://threads.net/@kasperhirvikoski/).
