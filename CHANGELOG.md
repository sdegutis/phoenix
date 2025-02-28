Changelog
=========

4.0.2 (master)
--------------

Release: dd.mm.yyyy

4.0.1
-----

Release: 11.6.2024

### Changes

- Upgrade Sparkle to 2.6.3.
- Xcode 15 is now required for building.

### Bug Fixes

- Fix `Space#moveWindows` on macOS Sonoma (14.5) ([#348](https://github.com/kasper/phoenix/issues/348), [#349](https://github.com/kasper/phoenix/issues/349)).

4.0.0
-----

Release: 19.5.2023

### New

- Improve modals by adding the ability to react to text commits, modal resizes and allowing to focus modals easily ([#304](https://github.com/kasper/phoenix/issues/304))! 🤖 Fix various bugs related to modals.
- Add support for tertiary mouse events ([#322](https://github.com/kasper/phoenix/issues/322)).

### Changes

- **Breaking:** Phoenix now requires macOS Mojave (10.14) or higher (required by Xcode 14).
- Upgrade Sparkle to 2.4.1.
- Xcode 14 is now required for building.

### Improvements

- Documentation improvements and clarifications. Add support for searching API documentation.
- Clarify in documentation you must keep a reference to a modal in order for it to stay active ([#326](https://github.com/kasper/phoenix/issues/326)).

### Bug Fixes

- Fix issue that caused input modals not to have a fixed width ([#302](https://github.com/kasper/phoenix/issues/302), [#324](https://github.com/kasper/phoenix/issues/324)).
- Fix issue that caused modals not to adjust to a custom weight if no font was provided ([#314](https://github.com/kasper/phoenix/issues/314)).
- Fix issue that caused modals to stay on screen if they were released from memory ([#326](https://github.com/kasper/phoenix/issues/326)).

### API

#### Events

- New: Event `mouseDidOtherClick` is triggered when the mouse did tertiary click ([#322](https://github.com/kasper/phoenix/issues/322)).
- New: Event `mouseDidOtherDrag` is triggered when the mouse did tertiary drag ([#322](https://github.com/kasper/phoenix/issues/322)).

#### Modal

- New: Property `didResize` callback function to call when the modal resizes ([#304](https://github.com/kasper/phoenix/issues/304)).
- New: Property `textDidCommit` callback function to call when the input modal’s text field is committed ([#304](https://github.com/kasper/phoenix/issues/304)).
- New: Function `focus()` focuses the modal and makes it the key window to receive events ([#304](https://github.com/kasper/phoenix/issues/304)).
- Change: Function `build(...)` will also bind the `origin` function to `didResize` so the modal will reposition automatically on resize ([#304](https://github.com/kasper/phoenix/issues/304)).
- Change: Function `show()` returns the modal ([#326](https://github.com/kasper/phoenix/issues/326)).

#### Window

- Change: Clarify function `screen()` can return `undefined` if a window is out of bounds of any screen ([#321](https://github.com/kasper/phoenix/issues/321)).

3.0.0
-----

Release: 26.2.2022

### New

- New app icon by [Parakeet](https://parakeet.co) ([#286](https://github.com/kasper/phoenix/issues/286))!
- Improved documentation! 👩🏼‍💻 The documentation is now powered by Docusaurus and hosted at https://kasper.github.io/phoenix/.
- Add support for an input modal 🚀 ([#163](https://github.com/kasper/phoenix/issues/163)).
- Add support to customise text alignment, font and colour in modals ([#158](https://github.com/kasper/phoenix/issues/158), [#242](https://github.com/kasper/phoenix/issues/242)).
- Add support for device sleep events ([#282](https://github.com/kasper/phoenix/issues/282)).
- Add support for moving windows to spaces in macOS 12.0 with `Space#moveWindows(...)` ([#289](https://github.com/kasper/phoenix/issues/289)).

### Changes

- **Breaking:** Phoenix now requires OS X El Capitan (10.11) or higher.
- **Breaking:** “Open at Login” is now using a launcher app instead of adding Phoenix to the deprecated login items of your user account. This setting will not be reflected anymore in the list and you can remove the app from it. You may need to enable this setting again for Phoenix to launch automatically after this update, depending on how you setup it the first time.
- Upgrade Sparkle to 2.1.0.
- Add support for Xcode 13.1 by properly importing the “Application Services” framework for Accessibility APIs ([#285](https://github.com/kasper/phoenix/issues/285)).

### Improvements

- Reload configuration automatically when “Accessibility” permission changes.
- Show more details about raised exception in the notification message.
- Close open modals when configuration is reloaded.

### Bug Fixes

- Fix crash if `Space#addWindows` or `Space#removeWindows` are passed an object that is not an instance of a Window.
- Fix issue that could cause the status bar item to be rendered multiple times when reloading the configuration.

### API

#### Events

- New: Event `deviceWillSleep` is triggered when the device will sleep ([#282](https://github.com/kasper/phoenix/issues/282)).
- New: Event `deviceDidWake` is triggered when the device did wake ([#282](https://github.com/kasper/phoenix/issues/282)).

#### Modal

- New: Property `hasShadow` for whether the modal has a shadow.
- New: Property `textAlignment` for the alignment of the text ([#158](https://github.com/kasper/phoenix/issues/158)).
- New: Property `font` for the font name used for the text ([#158](https://github.com/kasper/phoenix/issues/158)).
- New: Property `isInput` for whether the modal behaves as an input modal ([#163](https://github.com/kasper/phoenix/issues/163)).
- New: Property `inputPlaceholder` for the placeholder string that will be displayed when the input is empty ([#163](https://github.com/kasper/phoenix/issues/163)).
- New: Property `textDidChange` callback function to call when the input modal’s text field value changes ([#163](https://github.com/kasper/phoenix/issues/163)).
- New: Function `setTextColour(...)` or `setTextColor(...)` sets a custom text colour with the given RGBA values ([#158](https://github.com/kasper/phoenix/issues/158), [#242](https://github.com/kasper/phoenix/issues/242)).

#### Space

- New: Function `moveWindows(...)` moves the given windows to the space (macOS 10.13+) ([#289](https://github.com/kasper/phoenix/issues/289)).

2.6.8
-----

Release: 24.10.2021

### Changes

- Forward `console.log(...)` to `Phoenix.log(...)` for convenience.
- Log stack trace when passing an error to `Phoenix.log(...)` ([#181](https://github.com/kasper/phoenix/issues/181)).
- Upgrade Sparkle to 1.27.0.
- Xcode 13 is now required for building.

### Improvements

- Launch Console app when clicking a notification for an exception.
- Clarify the documentation about `Point`, `Size` and `Rectangle` being simple struct objects and not being extendable ([#273](https://github.com/kasper/phoenix/issues/273)).

2.6.7
-----

Release: 21.3.2021

### Changes

- Upgrade Sparkle to 1.26.0.

### Bug Fixes

- Fix issue that prevented window events to register for recently launched apps ([#264](https://github.com/kasper/phoenix/issues/264)).
- Fix issue that caused `App#mainWindow()` to return a broken Window instance when the app is for example minimised. The function will now correctly return `undefined` in such cases ([#269](https://github.com/kasper/phoenix/issues/269)).

2.6.6
-----

Release: 24.1.2021

### Bug Fixes

- Add temporary workaround for macOS bug that breaks focusing an individual window of an app in Big Sur ([#266](https://github.com/kasper/phoenix/issues/266), [#268](https://github.com/kasper/phoenix/pull/268)).

2.6.5
-----

Release: 29.11.2020

### Changes

- Add support for Apple Silicon.
- Improve first launch experience by removing custom alert before accessibility prompt and terminating Phoenix.
- Improve debug capabilities in Safari Web Inspector by listing configuration file sources ([#265](https://github.com/kasper/phoenix/pull/265)).
- Upgrade Sparkle to 1.24.0.
- Xcode 12 is now required for building.

2.6.4
-----

Release: 14.6.2020

### Changes

- Upgrade Sparkle to 1.23.0.

### Bug Fixes

- Fix issue that caused Phoenix to crash when binding keys with some keyboard layouts ([#196](https://github.com/kasper/phoenix/issues/196)).

2.6.3
-----

Release: 24.1.2020

### New

- Add support to load images from files which can be used as custom icons in modals ([#226](https://github.com/kasper/phoenix/issues/226)).
- Notarise Phoenix with Apple to pass Gatekeeper verification ([#241](https://github.com/kasper/phoenix/issues/241)).

### Changes

- Upgrade Lodash to 4.17.15 (from 4.17.5).
- Upgrade Sparkle to 1.22.0.
- Remove Grunt and use standard scripts to build library.
- Xcode 11 is now required for building.

### Bug Fixes

- Fix an issue that caused a crash if accessing screens for a space under some circumstances ([#231](https://github.com/kasper/phoenix/issues/231)).

### API

#### Keys

- New: Add support for `command`, `option` and `control` as additional key modifiers. This is purely syntactic sugar representing newer Apple keyboard layouts and they alias the existing `cmd`, `alt` and `ctrl` modifiers in this order ([#173](https://github.com/kasper/phoenix/issues/173)).

#### Events

- Change: Add key modifiers to mouse events ([#216](https://github.com/kasper/phoenix/issues/216), [#217](https://github.com/kasper/phoenix/pull/217)).

#### Image

- New: Function `fromFile(String path)` loads an image from the given path, the path is resolved before attempting to load the image, returns `undefined` if unsuccessful ([#226](https://github.com/kasper/phoenix/issues/226)).

2.6.2
-----

Release: 7.6.2018

### Changes

- Upgrade Lodash to 4.17.5 (from 4.17.4).
- Upgrade Sparkle to 1.19.0.

### API

#### Modal

- New: Property `animationDuration` defines the animation duration (in seconds) for showing and closing the modal, if the duration is set to `0` the animation will be disabled, by default `0.2` ([#203](https://github.com/kasper/phoenix/issues/203)).

#### App

- Change: Function `launch(...)` now supports a focus option to focus the app automatically on launch ([#211](https://github.com/kasper/phoenix/issues/211), [#212](https://github.com/kasper/phoenix/pull/212)).

2.6.1
-----

Release: 8.4.2018

### New

- Add support for one-time managed handlers for both keys and events ([#201](https://github.com/kasper/phoenix/issues/201)).

### API

#### Key

- New: Function `once(String key, Array<String> modifiers, Function callback)` constructs a managed handler for a key that is by default only triggered one time and then disabled, for more control you can explicitly return `false` from the callback function and the handler will not be disabled until you return something else, for arguments see `new Key(...)` ([#201](https://github.com/kasper/phoenix/issues/201)).

#### Event

- New: Function `once(String event, Function callback)` constructs a managed handler for an event that is by default only triggered one time and then disabled, for more control you can explicitly return `false` from the callback function and the handler will not be disabled until you return something else, for arguments see `new Event(...)` ([#201](https://github.com/kasper/phoenix/issues/201)).

2.6
---

Release: 25.12.2017

### New

- Add support for closing windows ([#184](https://github.com/kasper/phoenix/issues/184)).

### Changes

- Upgrade Sparkle to 1.18.1.
- Xcode 9 is now required for building.

### Improvements

- Improve documentation for the behaviour of `Window#raise()` ([#164](https://github.com/kasper/phoenix/pull/164)).

### Bug Fixes

- Fix an issue where `PHShebangPreprocessor` blocks due to a race condition ([reference](https://stackoverflow.com/a/39281558), [#167](https://github.com/kasper/phoenix/issues/167), [#169](https://github.com/kasper/phoenix/issues/169)).
- Fix an issue that removed Phoenix from the login items on reload when preference was set through the status bar menu ([#194](https://github.com/kasper/phoenix/issues/194)).

### API

#### Window

- New: Function `close()` closes the window, returns `true` if successful ([#184](https://github.com/kasper/phoenix/issues/184)).

2.5
---

Release: 22.1.2017

### New

- If you did not already know, macOS Sierra (10.12) has full support for the ECMAScript 6 standard and you can now use it with Phoenix! [Read](http://es6-features.org) a quick overview of the new features added to the language.
- Add support for getting the topmost window at a specified point ([#149](https://github.com/kasper/phoenix/issues/149)).
- Add “Edit configuration” status menu item ([#156](https://github.com/kasper/phoenix/pull/156)).
- Add support for mouse drag events ([#159](https://github.com/kasper/phoenix/issues/159)).

### Changes

- Lodash is upgraded to 4.17.4 (from 4.17.3).

### API

#### Events

- New: Event `mouseDidLeftDrag` is triggered when the mouse did left drag ([#159](https://github.com/kasper/phoenix/issues/159)).
- New: Event `mouseDidRightDrag` is triggered when the mouse did right drag ([#159](https://github.com/kasper/phoenix/issues/159)).

#### Window

- New: Function `at(Point point)` returns the topmost window at the specified point, can be `undefined` if no window is present at the given position ([#149](https://github.com/kasper/phoenix/issues/149)).

2.4
---

Release: 26.12.2016

### Changes

- Breaking: Underscore.js is replaced with [Lodash](https://lodash.com) (4.17.3) ([#89](https://github.com/kasper/phoenix/issues/89)).
- Xcode 8 is now required for building.

### Bug Fixes

- Fix an issue that caused inconsistencies with screens and spaces when “Displays have separate Spaces” option was disabled in macOS ([#130](https://github.com/kasper/phoenix/issues/130)).
- Fix an issue that prevented Phoenix from terminating after accessibility prompt ([#132](https://github.com/kasper/phoenix/issues/132)).
- Fix an issue that prevented preferences to be observed on launch ([#133](https://github.com/kasper/phoenix/issues/133)).
- Fix an issue that prevented task callbacks from performing actions on the main thread ([#137](https://github.com/kasper/phoenix/issues/137)).

### API

#### Phoenix

- Change: Function `log(...)` now supports multiple arguments ([#157](https://github.com/kasper/phoenix/issues/157)).

#### Task

- Change: Function `run(String path, Array arguments, Function callback)` can now be called without a callback ([#135](https://github.com/kasper/phoenix/issues/135)).

#### Space

- New: Function `screens()` returns all screens to which the space belongs to ([#130](https://github.com/kasper/phoenix/issues/130)).
- Deprecation: Function `screen()` is deprecated and will be removed in later versions, use `screens()` instead ([#130](https://github.com/kasper/phoenix/issues/130)).

#### Window

- New: Function `raise()` raises the window so it will be beneath the focused window, returns `true` if successful ([#151](https://github.com/kasper/phoenix/issues/151)).

2.3
---

Release: 6.8.2016

### New

- Modals have a new improved “vibrant” appearance and can now display icons as well as text. All the new options are described in the [API](https://github.com/kasper/phoenix/blob/2.3/API.md#16-modal) ([#126](https://github.com/kasper/phoenix/issues/126)).

### Improvements

- Callback for key is now called repeatedly when key is held down ([#119](https://github.com/kasper/phoenix/issues/119)).
- Improvements on exception handling. When present, the line and column number are also logged for exceptions.
- Performance improvements.

### Bug Fixes

- Fix issue that prevented `Window#setFrame(...)` to only set the origin for windows that cannot be resized ([#124](https://github.com/kasper/phoenix/issues/124)).

### API

#### Events

- Change: All mouse events receive the corresponding `Point`-object as the first argument for the callback function ([#125](https://github.com/kasper/phoenix/issues/125)).

#### Key

- Change: The callback function receives its handler as the first argument and as the second argument a boolean that indicates if the key was repeated (held down) ([#119](https://github.com/kasper/phoenix/issues/119)).

#### Modal

- New: Function `build(Map<String, AnyObject> properties)` builds a modal with the specified properties and returns it, `origin` should be a function that receives the frame for the modal as the only argument and returns a `Point`-object will be set as the origin for the modal ([#126](https://github.com/kasper/phoenix/issues/126)).
- New: Dynamic property `weight` defines the weight of the modal (in points), by default `24` ([#126](https://github.com/kasper/phoenix/issues/126)).
- New: Property `appearance` defines the appearance of the modal (`dark|light|transparent`), by default `dark` ([#126](https://github.com/kasper/phoenix/issues/126)).
- New: Dynamic property `icon` defines the icon displayed in the modal ([#126](https://github.com/kasper/phoenix/issues/126)).
- New: Dynamic property `text` defines the text displayed in the modal ([#126](https://github.com/kasper/phoenix/issues/126)).
- Change: Origin is now a dynamic property ([#126](https://github.com/kasper/phoenix/issues/126)).
- Deprecation: Property `message` is deprecated and will be removed in later versions, use `text` instead ([#126](https://github.com/kasper/phoenix/issues/126)).

#### Screen

- New: Function `frame()` returns the whole frame for the screen, bottom-left based origin ([#128](https://github.com/kasper/phoenix/issues/128)).
- New: Function `visibleFrame()` returns the visible frame for the screen subtracting the Dock and Menu from the frame when visible, bottom-left based origin ([#128](https://github.com/kasper/phoenix/issues/128)).
- New: Function `currentSpace()` returns the current space for the screen (macOS 10.11+, returns `undefined` otherwise) ([#120](https://github.com/kasper/phoenix/issues/120)).
- Change: Function `frameInRectangle()` is now `flippedFrame()` ([#128](https://github.com/kasper/phoenix/issues/128)).
- Change: Function `visibleFrameInRectangle()` is now `flippedVisibleFrame()` ([#128](https://github.com/kasper/phoenix/issues/128)).
- Deprecation: Function `frameInRectangle()` is deprecated and will be removed in later versions, use `flippedFrame()` instead ([#128](https://github.com/kasper/phoenix/issues/128)).
- Deprecation: Function `visibleFrameInRectangle()` is deprecated and will be removed in later versions, use `flippedVisibleFrame()` instead ([#128](https://github.com/kasper/phoenix/issues/128)).

#### App

- New: Function `icon()` returns the icon for the app ([#126](https://github.com/kasper/phoenix/issues/126)).

2.2.1
-----

Release: 13.7.2016

### Bug Fixes

- Fix issue that prevented `Window#others(...)` returning the correct windows based on the screen optional ([#116](https://github.com/kasper/phoenix/issues/116)).
- Fix crash when trying to traverse spaces ([#117](https://github.com/kasper/phoenix/issues/117)).

2.2
---

Release: 12.7.2016

### New

- Adds support for mouse events ([#90](https://github.com/kasper/phoenix/issues/90)).
- Phoenix now has a key–value storage that can be used to store values across reloads and reboots as JSON, see [Storage](https://github.com/kasper/phoenix/blob/2.2/API.md#6-storage) ([#97](https://github.com/kasper/phoenix/issues/97)).
- You can now run tasks asynchronously and retrieve their status, standard output and standard error. A new `Task`-object has been created to construct tasks, access their properties or to terminate the task, see its [API](https://github.com/kasper/phoenix/blob/2.2/API.md#15-task) ([#98](https://github.com/kasper/phoenix/issues/98)).
- Keys, events and timers are now constructed with relevant constructors instead of creating them through the global `Phoenix`-object ([#109](https://github.com/kasper/phoenix/issues/109)).
- Add support for British alternatives to the API ([#113](https://github.com/kasper/phoenix/issues/113)).

### Changes

- Breaking: Global `Command`-object has been removed, use `Task` instead as a direct replacement ([#98](https://github.com/kasper/phoenix/issues/98)).
- Breaking: You can now have multiple `Key`s for a single key combination. However, only one can be enabled at a time. Previously binding would only change the callback for an existing handler if a previously bound key combination was used again. Now, binding a key combination will always return a new unique handler. As before, this new handler is always enabled by default. Subsequently, any previous handler for the key combination will therefore be automatically disabled ([#99](https://github.com/kasper/phoenix/issues/99)).
- Breaking: Name and stylistic changes to the API ([#108](https://github.com/kasper/phoenix/issues/108)).
- Breaking: `KeyHandler` has been renamed to `Key`, `EventHandler` to `Event` and `TimerHandler` to `Timer` ([#109](https://github.com/kasper/phoenix/issues/109)).
- Debug configuration file suffix has changed from `-debug.js` to `.debug.js`.

### Improvements

- Improve API performance when system is under load ([#75](https://github.com/kasper/phoenix/issues/75)).
- Improve start performance ([#114](https://github.com/kasper/phoenix/issues/114)).

### API

#### Events

- New: Event `willTerminate` is triggered when Phoenix will terminate, use this event to perform any tasks before the application terminates.
- New: Event `mouseDidMove` is triggered when the mouse has moved ([#90](https://github.com/kasper/phoenix/issues/90)).
- New: Event `mouseDidLeftClick` is triggered when the mouse did left click ([#90](https://github.com/kasper/phoenix/issues/90)).
- New: Event `mouseDidRightClick` is triggered when the mouse did right click ([#90](https://github.com/kasper/phoenix/issues/90)).
- Change: Event `start` is now `didLaunch`.

#### Phoenix

- Deprecation: Function `bind(String key, Array<String> modifiers, Function callback)` has been removed, use constructor `new Key(String key, Array<String> modifiers, Function callback)` instead ([#109](https://github.com/kasper/phoenix/issues/109)).
- Deprecation: Function `on(String event, Function callback)` has been removed, use constructor `new Event(String event, Function callback)` instead ([#109](https://github.com/kasper/phoenix/issues/109)).
- Deprecation: Function `after(double interval, Function callback)` has been removed, use constructor `new Timer(double interval, boolean repeats, Function callback)` instead ([#109](https://github.com/kasper/phoenix/issues/109)).
- Deprecation: Function `every(double interval, Function callback)` has been removed, use constructor `new Timer(double interval, boolean repeats, Function callback)` instead ([#109](https://github.com/kasper/phoenix/issues/109)).

#### Key

- Change: Function `enable()` will disable any previous handler for the same key combination automatically ([#99](https://github.com/kasper/phoenix/issues/99)).

#### Event

- New: Function `disable()` disables the event handler.

#### Screen

- Change: Function `mainScreen()` is now simply `main()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `screens()` is now `all()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `windows()` now takes optionals `windows(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `visibleWindows()` has been removed, use `windows({ visible: true })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).

#### Space

- Change: Function `activeSpace()` is now simply `active()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `spaces()` is now `all()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `windows()` now takes optionals `windows(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `visibleWindows()` has been removed, use `windows({ visible: true })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).

#### Mouse

- Change: Function `moveTo()` is now simply `move()` ([#108](https://github.com/kasper/phoenix/issues/108)).

#### App

- Change: Function `focusedApp()` is now simply `focused()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `runningApps()` is now `all()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `windows()` now takes optionals `windows(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `terminate()` now takes optionals `terminate(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `visibleWindows()` has been removed, use `windows({ visible: true })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `forceTerminate()` has been removed, use `terminate({ force: true })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).

#### Window

- New: Function `neighbours(String direction)` returns windows to the direction (`west|east|north|south`) of the window ([#108](https://github.com/kasper/phoenix/issues/108)).
- New: Function `focusClosestNeighbour(String direction)` focuses the closest window to the direction (`west|east|north|south`) of the window, returns `true` if successful ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `focusedWindow()` is now simply `focused()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `windows()` is now `all(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `visibleWindowsInOrder()` is now `recent()` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Change: Function `otherWindowsOnAllScreens()` is now `others(Map<String, AnyObject> optionals)` ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `visibleWindows()` has been removed, use `all({ visible: true })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Function `otherWindowsOnSameScreen()` has been removed, use `others({ screen: window.screen() })` instead ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Functions `windowsToWest()`, `windowsToEast()`, `windowsToNorth()` and `windowsToSouth()` have been removed, use instead `neighbours('west')`, `neighbours('east')`, `neighbours('north')` and `neighbours('south')` respectively ([#108](https://github.com/kasper/phoenix/issues/108)).
- Deprecation: Functions `focusClosestWindowInWest()`, `focusClosestWindowInEast()`, `focusClosestWindowInNorth()` and `focusClosestWindowInSouth()` have been removed, use instead `focusClosestNeighbour('west')`, `focusClosestNeighbour('east')`, `focusClosestNeighbour('north')` and `focusClosestNeighbour('south')` respectively ([#108](https://github.com/kasper/phoenix/issues/108)).

2.1.2
-----

Release: 27.6.2016

### New

- Phoenix can now manage handlers for you. Instead of `Phoenix.bind`, `Phoenix.on`, `Phoenix.after` or `Phoenix.every` — use `Key.on`, `Event.on`, `Timer.after` and `Timer.every`. For more, see the [API](https://github.com/kasper/phoenix/blob/2.1.2/API.md#managing-handlers) ([#107](https://github.com/kasper/phoenix/issues/107)).

### Improvements

- Implement `setTimeout`, `setInterval`, `clearTimeout` and `clearInterval`. This also adds support for timing related functions from Underscore ([#92](https://github.com/kasper/phoenix/issues/92)).
- Make require throw an error if a file cannot be resolved ([#93](https://github.com/kasper/phoenix/issues/93)).
- Add support for ISO section `§`-key ([#102](https://github.com/kasper/phoenix/pull/102)).

### Bug Fixes

- Disable key handlers immediately to ensure that keys are unregistered before setting up a new context ([#94](https://github.com/kasper/phoenix/issues/94)).
- Fix crash caused by moving or deleting configuration directory while app is running ([#105](https://github.com/kasper/phoenix/issues/105)).

2.1.1
-----

Release: 29.4.2016

### Improvements

- Notify when preprocessing failed.

### Bug Fixes

- Fix an issue that prevented preprocessing due to incompatible paths between different shells ([#88](https://github.com/kasper/phoenix/issues/88)).

2.1
---

Release: 25.4.2016

### New

- Phoenix now supports Spaces! *These features are only supported on El Capitan (10.11) and upwards.* A new global `Space`-object has been created to control spaces, see the [API](https://github.com/kasper/phoenix/blob/2.1/API.md#17-space) ([#60](https://github.com/kasper/phoenix/issues/60)).
- Preferences can now be set programmatically through the API ([#67](https://github.com/kasper/phoenix/issues/67)).
- Phoenix can be run completely in the background, this also removes the status bar menu, see the `daemon`-preference in the [API](https://github.com/kasper/phoenix/blob/2.1/API.md#3-preferences) ([#68](https://github.com/kasper/phoenix/issues/68)).
- You can now create timers to achieve delays and timed events. A new `TimerHandler`-object has been created to control timers, see its [API](https://github.com/kasper/phoenix/blob/2.1/API.md#13-timerhandler). See the functions `Phoenix.after(double interval, Function callback)` and `Phoenix.every(double interval, Function callback)` in the [API](https://github.com/kasper/phoenix/blob/2.1/API.md#5-phoenix) to create timers ([#77](https://github.com/kasper/phoenix/issues/77)).

### Changes

- Upgrade Sparkle to 1.14.0. This also fixes the HTTP MITM-vulnerability discovered in Sparkle — though Phoenix was never vulnerable since we use HTTPS to secure updates.

### Improvements

- Adjust latency of context reloads on configuration file changes to limit race conditions ([#83](https://github.com/kasper/phoenix/issues/83)).
- Objects that implement `Iterable` can be traversed. Namely, `Screen` and `Space`.
- All handlers now receive their handlers as the last argument for the callback function.
- Improvements to memory management and other small improvements.

### Bug Fixes

- Improve error handling in preprocessing ([#65](https://github.com/kasper/phoenix/issues/65)).
- Fix an issue that prevented an exception raised in a handler callback to be caught and reported ([#70](https://github.com/kasper/phoenix/issues/70)).
- Fix an issue that prevented setting the frame for a window correctly while moving it to a smaller screen ([#84](https://github.com/kasper/phoenix/issues/84)).

### API

#### Events

- New: Event `spaceDidChange` is triggered when the active space has changed.

#### Phoenix

- New: Function `after(double interval, Function callback)` creates a timer that fires the callback once after the given interval (in seconds) and returns the handler, you must keep a reference to the handler in order for your callback to get called, the callback function receives its handler as the only argument.
- New: Function `every(double interval, Function callback)` creates a timer that fires the callback repeatedly until stopped using the given interval (in seconds) and returns the handler, you must keep a reference to the handler in order for your callback to get called, the callback function receives its handler as the only argument.
- New: Function `set(Map<String, AnyObject> preferences)` sets the preferences from the given key–value map, any previously set preferences with the same key will be overridden.
- Change: The callback for function `bind(String key, Array<String> modifiers, Function callback)` now receives its handler as the only argument, previously the callback received no arguments.
- Change: The callback for function `on(String event, Function callback)` now receives its handler as the last argument.

#### Screen

- New: Function `identifier()` returns the UUID for the screen ([#79](https://github.com/kasper/phoenix/issues/79)).
- New: Function `spaces()` returns all spaces for the screen (OS X 10.11+, returns an empty list otherwise).

#### Window

- New: Function `isFullScreen()` returns `true` if the window is a full screen window ([#60](https://github.com/kasper/phoenix/issues/60), [#80](https://github.com/kasper/phoenix/issues/80)).
- New: Function `spaces()` returns the spaces where the window is currently present (OS X 10.11+, returns an empty list otherwise).
- New: Function `setFullScreen(boolean value)` sets whether the window is full screen ([#60](https://github.com/kasper/phoenix/issues/60), [#80](https://github.com/kasper/phoenix/issues/80)).

2.0.1
-----

Release: 12.12.2015

### Changes

- Amend license regarding the Phoenix icon assets contributed by Jason Milkins for not being under the MIT License ([#61](https://github.com/kasper/phoenix/pull/61)).

### Bug Fixes

- Fix issue where `Mouse.location()` and `Mouse.moveTo(Point point)` used different coordinate origins. Both now correctly use top-left as the origin ([#58](https://github.com/kasper/phoenix/issues/58)).
- Support shells (e.g. Fish) that do not support `-cl` option shorthand in preprocessing ([#57](https://github.com/kasper/phoenix/pull/57)).

2.0
---

Release: 28.11.2015

### New

- Phoenix now supports events! See the [API](https://github.com/kasper/phoenix/blob/2.0/API.md#2-events). To bind an event to a callback function, you call the `on`-function for the `Phoenix`-object.
- You may now use JavaScript [preprocessing](https://github.com/kasper/phoenix/blob/2.0/API.md#preprocessing) and languages such as CoffeeScript to write your Phoenix-configuration ([#45](https://github.com/kasper/phoenix/pull/45)). Thanks [@shayne](https://github.com/shayne/)!
- Updates are now delivered and installed through Sparkle ([#50](https://github.com/kasper/phoenix/issues/50)).
- Phoenix now supports additional configuration locations. In addition to `~/.phoenix.js`, you may also use `~/Library/Application Support/Phoenix/phoenix.js` or `~/.config/phoenix/phoenix.js` if you prefer to do so ([#52](https://github.com/kasper/phoenix/issues/52)).

### Changes

- Phoenix has been rewritten and refactored from the ground up. This also means that Phoenix now requires OS X Yosemite (10.10) or higher. Xcode 7 is now required for building.
- Supports OS X El Capitan (10.11).
- Underscore.js is upgraded to 1.8.3 (from 1.5.2). This may change existing behaviour related to Underscore.
- Global `api`-object is now called `Phoenix`.
- Global `MousePosition`-object is now called `Mouse`.
- `Hotkey`-object is now called `KeyHandler` and its properties have changed. See the [API](https://github.com/kasper/phoenix/blob/2.0/API.md#9-keyhandler).
- The concept of `Alerts` has been deprecated. A new global `Modal`-object has been created to display messages as modals. See the [API](https://github.com/kasper/phoenix/blob/2.0/API.md#11-modal).
- A new `EventHandler`-object has been created to handle events. See the [API](https://github.com/kasper/phoenix/blob/2.0/API.md#10-eventhandler).
- A new global `Command`-object has been created to run UNIX-commands. See the [API](https://github.com/kasper/phoenix/blob/2.0/API.md#12-command).

### Improvements

- A new subtler status item icon.
- Alerts are now delivered through Notification Center and logged to Console for easier debugging.
- Now reloading the context gives no alert unless an error is encountered.
- Objects that implement `Identifiable` can be identified and compared.

### Bug Fixes

- Support non-unicode keyboards ([#34](https://github.com/kasper/phoenix/issues/34)).
- Support relative requires with symlinks in configuration ([#42](https://github.com/kasper/phoenix/pull/42)).

### API

#### Phoenix

- New: Function `on(String event, Function callback)` binds an event to a callback function.
- New: Function `notify(String message)` delivers a message to the Notification Center.
- Change: Function `launch(String appName)` has moved to the global `App`-object.
- Change: Function `runCommand(String commandPath, Array arguments)` has moved to a new global `Command`-object and is now called `run(String path, Array arguments)`.
- Deprecation: Function `alert(String message, double durationInSeconds)` has been removed, use `Modal` to display messages as modals.
- Deprecation: Function `cancelAlerts()` has been removed, you must keep references to modals yourself to close them.
- Deprecation: Function `setTint(Array<double> red, Array<double> green, Array<double> blue)` has been removed with no replacement.

#### KeyHandler

- New: KeyHandler now implements `Identifiable`.
- Change: *You must now keep a reference to the handler*, otherwise your callback will not get called.
- Change: Special keys are now camelCased (case sensitive) instead of underscored. See changed [keys](https://github.com/kasper/phoenix/blob/2.0/API.md#special-keys).
- Change: Keys for keypad are now prefix with `keypad` instead of `pad`.

#### Screen

- New: Screen now implements `Identifiable`.
- New: Function `mainScreen()` returns the screen containing the window with the keyboard focus.
- New: Function `screens()` returns all screens.
- New: Function `windows()` returns all windows for the screen.
- New: Function `visibleWindows()` returns all visible windows for the screen.
- Change: For clarity, functions `frameIncludingDockAndMenu()` and `frameWithoutDockOrMenu()` are now `frameInRectangle()` and `visibleFrameInRectangle()`, respectively.
- Change: Functions `nextScreen()` and `previousScreen()` are now simply `next()` and `previous()`.

#### Mouse

- New: Function `moveTo(Point point)` returns a boolean value for determining success.
- Change: Functions `capture()` and `restore(Point point)` are now called `location()` and `moveTo(Point point)`.

#### App

- New: App now implements `Identifiable`.
- New: All actions return a boolean value for determining success.
- New: Function `get(String appName)` returns the running app with the given name.
- New: Function `launch(String appName)` now returns the launched app if successful.
- New: Function `focusedApp()` returns the focused app.
- New: Function `isActive()` returns whether the app is currently frontmost.
- New: Function `isTerminated()` returns whether the app has been terminated.
- New: Function `mainWindow()` returns the main window for the app.
- New: A new function `focus()` focuses the app and its windows.
- Change: Property `pid` is now a function called `processIdentifier()`.
- Change: Function `title()` is now called `name()`.
- Change: Function `allWindows()` is now simply `windows()`.
- Change: Functions `kill()` and `kill9()` are now `terminate()` and `forceTerminate()`, respectively.

#### Window

- New: Window now implements `Identifiable`.
- New: All actions return a boolean value for determining success.
- New: Function `isMain()` returns whether the window is the main window for its app.
- New: Function `isVisible()` returns whether the window is a normal and unminimised window that belongs to an unhidden app.
- Change: Function `allWindows()` is now simply `windows()`.
- Change: Function `visibleWindowsMostRecentFirst()` is renamed to `visibleWindowsInOrder()` for clarity.
- Change: Function `isNormalWindow()` is now simply `isNormal()`.
- Change: Function `isWindowMinimized()` is now simply `isMinimized()`.
- Change: Function `unMinimize()` is now `unminimize()`.
- Change: Function `focusWindow()` is now `focus()`.
- Change: Alignment functions `windowsToWest(), windowsToEast(), windowsToNorth(), windowsToSouth()` now correctly return windows relative to the window and not relative to the focused window. To achieve the previous behaviour you need chain these with the `focusedWindow()`-accessor. This also affects `focusClosestWindowInWest(), focusClosestWindowInEast(), focusClosestWindowInNorth(), focusClosestWindowInSouth()`-functions.
- Change: Functions `focusWindowLeft(), focusWindowRight(), focusWindowUp(), focusWindowDown()` are now `focusClosestWindowInWest(), focusClosestWindowInEast(), focusClosestWindowInNorth(), focusClosestWindowInSouth()`, respectively.
