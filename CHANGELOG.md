# AxonifyLib Changelog
  
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
