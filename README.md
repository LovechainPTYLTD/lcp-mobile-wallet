O<sub>byte</sub> is a wallet for storage and transfer of decentralized value.  See [obyte.org](https://obyte.org/).

## Binary Downloads

[Obyte.org](https://obyte.org/)

## Main Features

TBD

## Installation

download and install NVM. the script will install automatically.:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

make sure to follow the instructions at the end of the installation script.
with nvm install node version 8.15.0
nvm install 8.15.0
nvm use 8.15.0


Install [bower](http://bower.io/) and [grunt](http://gruntjs.com/getting-started) if you haven't already:

```sh
npm install -g bower
npm install -g grunt-cli
```

Build LCP:

```sh
bower install
npm install
grunt
```

After first run, you'll likely encounter runtime error complaining about node_sqlite3.node not being found, copy the file from the neighboring directory to where the program tries to find it, and run again (e.g. from `obyte-gui-wallet/node_modules/sqlite3/lib/binding/node-v47-darwin-x64` to `obyte-gui-wallet/node_modules/sqlite3/lib/binding/node-webkit-v0.14.7-darwin-x64`). If that didn't work, copy node_sqlite3.node from node_modules folder, which is got installed with installer file from obyte.org website.


## Build O<sub>byte</sub> App Bundles

All app bundles will be placed at `../obytebuilds` dir, so create it first: `mkdir -p ../obytebuilds`


### Android
- Install jdk1.8 (9 and higher won't work)
- Install Android SDK (from Android Studio)
- Run `make android-debug`
  * In case of `could not find gradle wrapper within android sdk` error, download Android SDK tools package v25:
    * http://dl-ssl.google.com/android/repository/tools_r25.2.5-macosx.zip
    * http://dl-ssl.google.com/android/repository/tools_r25.2.5-windows.zip

  and extract to android_sdk_folder/ (should replace ./tools folder).

### iOS

- Install Xcode 7 (or newer)
- Install Cordova 6 `npm install cordova@6 -g`
- Run `make ios-debug`
  * In case of ios-deploy missing error: `npm install -g ios-deploy`
  * In case of `DeviceSupport` missing error, run `cd /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/ && sudo ln -s 10.3.1\ \(14E8301\)/ 10.3`
  * If you encounter 'bitcore' not found after app launch, install it also `npm install bitcore-lib` and remove `../bytebalbuilds/project-IOS` folder completely, then rerun make again.
  * On code signing error, open Xcode project `../obytebuilds/project-IOS/platforms/ios/Byteball.xcodeproj` in Xcode, open project properties, select Byteball target and set your AppleID account as a team. Xcode may also ask you to change bundle identifier to be unique, just append any random string to 'org.byteball.wallet' bundle identifier.

### macOS

- `grunt desktop`
- copy `node_modules` into the app bundle ../obytebuilds/Obyte/osx64/Obyte.app/Contents/Resources/app.nw, except those that are important only for development (karma, grunt, jasmine)
- `grunt dmg`

### Windows

- `grunt desktop`
- copy `node_modules` into the app bundle ../obytebuilds/Obyte/win64, except those that are important only for development (karma, grunt, jasmine)
- `grunt inno64`

### Linux

- `grunt desktop`
- copy `node_modules` into the app bundle ../obytebuilds/Obyte/linux64, except those that are important only for development (karma, grunt, jasmine)
- `grunt linux64`


## About O<sub>byte</sub>

TBD

## O<sub>byte</sub> Backups and Recovery

O<sub>byte</sub> uses a single extended private key for all wallets, BIP44 is used for wallet address derivation.  There is a BIP39 mnemonic for backing up the wallet key, but it is not enough.  Private payments and co-signers of multisig wallets are stored only in the app's data directory, which you have to back up manually:

* macOS: `~/Library/Application Support/byteball`
* Linux: `~/.config/byteball`
* Windows: `%LOCALAPPDATA%\byteball`


## Translations

O<sub>byte</sub> uses standard gettext PO files for translations and [Crowdin](https://crowdin.com/project/byteball) as the front-end tool for translators. To join our team of translators, please create an account at [Crowdin](https://crowdin.com) and translate the O<sub>byte</sub> documentation and application text into your native language.

To download and build using the latest translations from Crowdin, please use the following commands:

```sh
cd i18n
node crowdin_download.js
```

This will download all partial and complete language translations while also cleaning out any untranslated ones.


## Support

* [GitHub Issues](https://github.com/byteball/obyte-gui-wallet/issues)
  * Open an issue if you are having problems with this project
* [Email Support](mailto:byteball@byteball.org)

## Credits

The GUI is based on [Copay](https://github.com/bitpay/copay), the most beautiful and easy to use Bitcoin wallet.

## License

MIT.