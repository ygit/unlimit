# Unlimit 🚀📲 [![Gem Version](https://badge.fury.io/rb/unlimit.svg)](https://badge.fury.io/rb/unlimit)

Unlimit is a simple tool to quickly run your app on your device without worrying about the 100 device limit per developer account set by Apple. It achieves this by temporarily switching your Xcode Project to your [free](https://github.com/biocross/unlimit#do-i-require-a-paid-apple-developer-account-to-use-this) personal team (`Personal Team`).

> In a nutsell, unlimit fixes this:

<img width="350" src="https://github.com/biocross/unlimit/raw/master/images/max_devices.png" alt="Xcode Device Limit Reached Error">

**Note that all changes unlimit makes to your project are local on your mac, and do not in anyway affect the configuration on your Apple Developer Portal.**

### Why can't I just do it myself?

Well, you can, if your project is simple. However, if your project has capabilities like **Push Notifications**, **Background Modes** & **App Extensions**, things get complicated, since these require you to configure your `Personal Team` with all these entitlements. Unlimit gets rid of all this mess, and gets you quickly up and running on your device.

### What's the catch?

Well, since unlimit temporarily removes capabilities like **App Extensions, Push Notifications** & more from your project, you **cannot** test these features on your device when using your personal team.

### How do I undo unlimit's changes?

We recommend you run unlimit when you have no staged changes, so that you can simple go back by running `git reset --hard` when you're done testing on your device.

## Installation

If your iOS/Mac project does not have a `Gemfile` yet, [learn how to set it up here](https://www.mokacoding.com/blog/ruby-for-ios-developers-bundler/). It's highly recommended you use [**bundler**](https://bundler.io/) to maintain consistent versions of tools like `cocoapods`, `fastlane` etc within your team. 

To use unlimit, add this line to your app's Gemfile:

```ruby
gem 'unlimit'
```

And then install it using [bundler](https://bundler.io/) by executing:

    $ bundle install


## Usage

After installing the gem, just run:

    $ bundle exec unlimit

and unlimit will do it's magic.

## Parameters
All these parameters are optional, as unlimit can **autodetect** most of these. You can use these when unlimit is unable to figure them out, or to pass in overrides.

| Parameter | Description | Example |
| --- | --- | --- |
| `project` | The **.xcodeproj** project file to use | `--project MyApp.xcodeproj` |
| `target`  | The **app target** you want to run on your device | `--target MyApp` |
| `plist`   | The **path** to your app's **Info.plist** file | `--plist MyApp/MyApp-Info.plist` |
| `team_id`   | The Code Signing **Team ID** to use | `--team_id A1B2C3D4E5A` |
| `keep_fabric`   | Unlimit automatically disables Fabric's build phase script, to avoid the annoying `New app ID added` email sent by Fabric. Use this flag for keep the Fabric script. (Note: This does not affect Fabric/Crashlytics functionality, only disables it's dSYM uploading shell script) | `--keep_fabric` |
| `version`   | Print the current unlimit version you're using and exit | `--version` |

## Contributing

Bug reports and pull requests are welcome. Any feedback or feature suggesions are also encouraged.

## More FAQs

### Do I require a paid apple developer account to use this?

No, you can get a `personal team` using a free Apple Developer Account, since Apple now allows testing on device with a free developer accounts as well. As apple puts it: 

> Xcode 7 and Xcode 8 allow you to select the free personal team provided with your Apple ID for signing your app. This team allows you to build apps for your personal use on devices owned by you, but it does not allow you to code sign apps destined for the App Store or for enterprise use.

>You can identify this account by looking in the accounts tab of the Xcode preferences. It is also displayed in the team menu displayed in a target's general build settings. Your personal account will be the account with the string '(Personal Team)' beside the name.

Source: https://developer.apple.com/library/archive/qa/qa1915/_index.html

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
