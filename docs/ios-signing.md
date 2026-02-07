# iOS signing setup

This project expects manual signing assets to be provided as GitHub secrets.

## Apple Developer

1) Create an App ID that matches your bundle identifier.
2) Create an App Store Connect app for the bundle ID.
3) Create an Apple Distribution certificate and download it.
4) Create an App Store provisioning profile using the App ID + certificate.

## App Store Connect API key

1) Create an API key in App Store Connect.
2) Download the `.p8` key file.
3) Record the Key ID and Issuer ID.

## Export to GitHub secrets

1) Export the certificate as `.p12` and keep the password.
2) Base64-encode `.p12` and `.mobileprovision`.
3) Add the following secrets in GitHub:

- `IOS_BUNDLE_ID`
- `IOS_TEAM_ID`
- `IOS_PROVISION_PROFILE_NAME`
- `IOS_DIST_P12_BASE64`
- `IOS_DIST_P12_PASSWORD`
- `IOS_PROVISION_PROFILE_BASE64`
- `APPSTORE_API_KEY_ID`
- `APPSTORE_API_ISSUER_ID`
- `APPSTORE_API_PRIVATE_KEY`
