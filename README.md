Spectrum
========

[![Swift 2.1](https://img.shields.io/badge/Swift-2.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Platforms OS X | iOS](https://img.shields.io/badge/Platforms-OS%20X%20%7C%20iOS-lightgray.svg?style=flat)](https://developer.apple.com/swift/)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-Compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![License MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Travis](https://img.shields.io/badge/Build-Passing-4BC51D.svg?style=flat)](https://travis-ci.org/Zewo/Spectrum)
[![codecov.io](http://codecov.io/github/Zewo/Spectrum/coverage.svg?branch=master)](http://codecov.io/github/Zewo/Spectrum?branch=master)

**Spectrum** provides POSIX Regular Expressions for **Swift 2**.

## Features

- [x] No `Foundation` dependency (**Linux ready**)
- [x] Matches
- [x] Groups
- [x] Replace

## Usage

```swift
let regex = try! Regex(pattern: "hello")
regex.matches("hello") // true
regex.matches("bye") // false

let regex = try! Regex(pattern: "(hello)")
regex.groups("hello") // ["hello"]
regex.groups("bye") // []

let regex = try! Regex(pattern: "(hello) (world)")
let groups = regex.groups("hello world") // ["hello", "world"]
    
let regex = try! Regex(pattern: "hello")
regex.replace("hello world", withTemplate: "bye") // "bye world"
```

## Installation

### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
$ brew update
$ brew install carthage
```

To integrate **Spectrum** into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "Zewo/Spectrum"
```

### Manually

If you prefer not to use a dependency manager, you can integrate **Spectrum** into your project manually.

#### Embedded Framework

- Open up Terminal, `cd` into your top-level project directory, and run the following command "if" your project is not initialized as a git repository:

```bash
$ git init
```

- Add **Spectrum** as a git [submodule](http://git-scm.com/docs/git-submodule) by running the following command:

```bash
$ git submodule add https://github.com/Zewo/Spectrum.git
```

- Open the new `Spectrum` folder, and drag the `Spectrum.xcodeproj` into the Project Navigator of your application's Xcode project.

    > It should appear nested underneath your application's blue project icon. Whether it is above or below all the other Xcode groups does not matter.

- Select the `Spectrum.xcodeproj` in the Project Navigator and verify the deployment target matches that of your application target.
- Next, select your application project in the Project Navigator (blue project icon) to navigate to the target configuration window and select the application target under the "Targets" heading in the sidebar.
- In the tab bar at the top of that window, open the "General" panel.
- Click on the `+` button under the "Embedded Binaries" section.
- You will see two different `Spectrum.xcodeproj` folders each with two different versions of the `Spectrum.framework` nested inside a `Products` folder.

    > It does not matter which `Products` folder you choose from, but it does matter whether you choose the top or bottom `Spectrum.framework`.

- Select the top `Spectrum.framework` for OS X and the bottom one for iOS.

    > You can verify which one you selected by inspecting the build log for your project. The build target for `Spectrum` will be listed as either `Spectrum iOS` or `Spectrum OSX`.

- And that's it!

> The `Spectrum.framework` is automagically added as a target dependency, linked framework and embedded framework in a copy files build phase which is all you need to build on the simulator and a device.

License
-------

**Spectrum** is released under the MIT license. See LICENSE for details.
