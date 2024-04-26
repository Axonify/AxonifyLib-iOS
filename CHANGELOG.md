# AxonifyLib Changelog

## 4.0.0
### Build Changes
- AxonifyLibXCFramework is now built with Xcode 15
- The minimum supported iOS version (deployment target) is now iOS 12
- A [privacy manifest](https://developer.apple.com/documentation/bundleresources/privacy_manifest_files) has been added, including [required reason APIs](https://developer.apple.com/documentation/bundleresources/privacy_manifest_files/describing_use_of_required_reason_api) to satisfy Apple's latest requirements

### API
- The `KeychainHelper` interface has been removed

## 3.0.0

### Functionality Changes
- Support for login using OpenID Connect (configured in Axonify AdminZone) if the new `AxonifyAuthenticationDelegate` is implemented.

### API Changes
- `AxonifyOAuthDelegate` has been removed and replaced with `AxonifyAuthenticationDelegate`
    - The `AxonifyWebViewController` `accessTokenLoaded(accessToken:)` and `errorLoadingAccessToken(error:)` methods have been removed, in favour of a `completion` callback using `Result` types in the new `AxonifyAuthenticationDelegate.authenticate(sender:identityProvider:completion:)` method.
    - `OAuthProviderType` has been removed. The new equivalent is `IdentityProvider`, which provides parameters for authenticating with an OpenID Connect identity provider. 
- `AxonifyWebViewController` initializers have been simplified to a single initializer with default parameter values.
    - All existing initializer combinations are still supported, there should be no behaviour changes as a result of this change.

## 2.1.0

### Functionality Changes
- Disables link preview and menu on in-app links

### API Changes
*None*
  
## 2.0.0

### New Features
- Support for custom SAML configurations on managed devices via AppConfig (MDM)

### Build Changes
- AxonifyLibXCFramework is now built with Xcode 14
- The minimum supported iOS version (deployment target) is now iOS 11

### API Changes
- `AxonifyWebViewController.clearAppData()` has a new `reset: Bool` parameter, which defaults to `true` (preserving previous behaviour)
    - Calling `clearAppData(reset: false)` will clear the cached app data and stored credentials, but will not trigger an app reset and call to `AxonifyWebViewControllerDelegate.readyToLoad(sender:)`, which was previous behaviour.
- The return type of `TenantService.getUrlStringForTraining()` is now an optional `String?`, changed from `String`
- `AxonifyWebViewController.splashScreenColor` is now non-optional, with a default value of `UIColor.black`
- `AxonifyError` has a new `malformedURL` case, thrown when a URL may have a valid tenant ID, but is malformed in other ways

### Other Changes
- Fixes various crashes and potential crashes

## 1.0.0
Initial XCFramework release.
