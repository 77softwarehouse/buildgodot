# buildgodot

Minimal Godot project for iOS TestFlight CI.

## Local setup

1) Open the project in Godot and run it to verify the scene.
2) Update `export_presets.cfg` with your bundle identifier.
3) In Godot, confirm the iOS export preset settings (bundle ID, version, icons).

## GitHub Actions secrets

Add the following repository secrets:

- `IOS_BUNDLE_ID` (e.g., `com.example.buildgodot`)
- `IOS_TEAM_ID` (Apple Developer Team ID)
- `IOS_PROVISION_PROFILE_NAME` (profile name shown in Xcode/Apple portal)
- `IOS_DIST_P12_BASE64` (base64-encoded distribution certificate `.p12`)
- `IOS_DIST_P12_PASSWORD` (password for the `.p12`)
- `IOS_PROVISION_PROFILE_BASE64` (base64-encoded provisioning profile `.mobileprovision`)
- `APPSTORE_API_KEY_ID`
- `APPSTORE_API_ISSUER_ID`
- `APPSTORE_API_PRIVATE_KEY` (contents of the `.p8` key file)

To encode files:

- `base64 -i ios_distribution.p12 | pbcopy`
- `base64 -i profile.mobileprovision | pbcopy`

## CI build trigger

Any commit pushed to `main` triggers the `iOS TestFlight` workflow:

1) Downloads Godot + export templates.
2) Exports an Xcode project from `export_presets.cfg`.
3) Builds and archives using the signing assets.
4) Exports an `.ipa`.
5) Uploads the `.ipa` to TestFlight.

## TestFlight verification

After the workflow completes, wait for App Store Connect processing, then verify the build appears in TestFlight for internal testing.
