# V iOS Bundler
A generic utility to bundle and sign iOS binaries without using Xcode on macOS.

## Building

Vib is built using [V](https://github.com/vlang/v), hence you need to install the V compiler to build it.
```
git clone https://github.com/vlang/v
cd v
make
sudo ./v symlink  # Optional, adds V to your path so you can call `v` from anywhere.
```
Once V is installed, simply build Vib using `v .`

## Usage

Bundle and sign a binary using `vib <binary path>`. The config file should have the same name as the binary but with `.vib` appended to the filename.

### Example Config

```
bundle_name=HelloWorld
bundle_id=app.vlang.helloworld
bundle_version=1
display_name=Hello World
team_id=APPLETEAMID
codesign_identity=Apple Development: Leah Lundqvist (IDENTITY_ID)
provisioning_profile=app_vlang_helloworld.mobileprovision
```

## Wizards

To enable automated provisioning and certificate creation, you need to create an API key on [App Store Connect](https://appstoreconnect.apple.com/access/api). Save the key file to `~/.vib` and create a file called `config.vib` in the same directory containing
```
issuer_id=<App Store Connect Issuer ID>
key_id=<Key ID>
key_file=AuthKey_<Key ID>.p8
```

### Certificate Wizard

Codesign certificates are required to bundle using vib as it's also required to run an app on a physical device.

```
vib certificate
```

### Provisioning Profile Wizard

```
vib provision
```