[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

# Localize-Swift
Localize-Swift is a simple framework that improves i18n and localization in Swift iOS apps - providing cleaner syntax and in-app language switching.

<p align="center"><img src="http://i.imgur.com/vsrpqBt.gif" width="242" height="425"/></p>

## Features

- Keep the Localizable.strings file your app already uses.
- Allow your users to change the app's language without changing their device language.
- Use Localized(key) instead of NSLocalizedString(key,comment) - a more Swift-friendly syntax.
- Generate your strings with a new genstrings python script that recognises Localized(key). 

## Usage

Import Localize at the top of each Swift file that will contain localized text:
```
import Localize
```

Wrap every string in Localized():
```
textLabel.text = Localized("Hello World")
```

To get an array of available localizations:
```
Localize.availableLanguages()
```

To change the current language:
```
Localize.setCurrentLanaguage("fr")
```

To update the UI in the viewcontroller where a language change can take place, observe LCLLanguageChangeNotification :
```
NSNotificationCenter.defaultCenter().addObserver(self, selector: "setText", name: LCLLanguageChangeNotification, object: nil)
```

To reset back to the default app language:
```
Localize.resetCurrentLanaguageToDefault()
```

## genstrings

To support this new Localized("string") syntax, Localize-Swift includes a custom genstrings python script.

Copy the genstrings.py file into your project's root folder and run with

```
python genstrings.py
```

This will print the collected strings in the terminal. Select and copy to your default Localizable.strings.


### Setting up with Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
$ brew update
$ brew install carthage
```

To integrate Localize-Swift into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "marmelroy/Localize-Swift"
```

### Setting up with [CocoaPods](http://cocoapods.org/?q=libPhoneNumber-iOS)
```
source 'https://github.com/CocoaPods/Specs.git'
pod 'Localize-Swift', '~> 0.0.1'
```
