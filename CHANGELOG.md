# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 0.5.0-alpha - unreleased

This is an alpha version! The changes listed here are not final.

### Added
- Add API-managed payment buttons behind a feature flag that is not yet enabled. Once it is on, you can connect a PayPal account from WordPress, create and manage payment links without leaving the editor, choose a Button, Link, or QR format, and pick a Light, Auto, or Dark style preset.

### Changed
- General: Update minimum WordPress version to 6.9.
- General: Update minimum WordPress version to 7.0.
- Internal: No longer require automattic/jetpack-changelogger as a per-project dev dependency.
- Move the payment button's product form into the block settings sidebar, and label its primary button Create New or Save instead of repeating the display format.
- Remove unneeded development and documentation files from the published plugin.
- Tested up to WordPress 7.0.
- Tested up to WordPress 7.1.
- Updated package dependencies.
- Update package dependencies.

### Removed
- Updated PHP version requirements to PHP 7.4 or newer.

### Fixed
- Allow product descriptions up to PayPal's real 2048-character limit, instead of cutting them off at 256.
- Break the PayPal disconnect confirmation into a short summary and a list, so its consequences are readable at a glance.
- Close PayPal's onboarding window with the Escape key or its Close button, instead of reloading the editor and losing unsaved changes.
- Close the PayPal onboarding popup automatically when it returns, instead of leaving it open on a wp-admin screen.
- Complete PayPal onboarding using PayPal's own onboarding SDK, so connecting an account finishes instead of stopping at "Merchant integration info not available".
- Connect a PayPal account in a separate window, so finishing onboarding no longer reloads the editor and discards an unsaved post.
- Discard a PayPal connection that fails its final checks, instead of leaving the site looking connected while reporting an error.
- Encode the PayPal payment link in the QR code behind the button's Show Link or QR Code toggle, instead of the page the button sits on.
- Fix "Connect with PayPal" always failing with "Request is not well-formed, syntactically incorrect, or violates schema." The seller nonce was 43 characters, one below the minimum PayPal enforces.
- Fix "Connect with PayPal" failing its final checks. The setup request never asked PayPal for Payment Links & Buttons access, which every button needs.
- Fix "Connect with PayPal" failing with a 404, and create the onboarding referral through WordPress.com so PayPal platform credentials never reach the site.
- Fix an error from PayPal when product options have their own prices. The product price is now optional in that case, and every option in the group must be priced.
- Fix editing a payment button reporting an error after the edit saved. PayPal answers a successful update with 204 No Content and the API client expected 200.
- Fix onboarding leaving the site connected but reporting "Merchant integration info not available". The merchant ID PayPal returns on the redirect was never saved.
- Fix tax collection turning itself off. An empty tax name made the block and then the REST route throw the whole tax away.
- Fix Update deleting payment configuration set outside the block. An update is a full replacement at PayPal, so a SKU, shipping rate, handling fee or discount set anywhere else was silently dropped, and address collection was forced back on.
- Go straight to the API credentials step on a site with no WordPress.com connection, instead of offering Connect with PayPal.
- Include PayPal's own error and debug ID when Payment Links & Buttons access is refused, instead of guessing at the cause.
- Include the PayPal partner attribution code in every copied and emailed payment link, matching the link the published button uses.
- Keep the PayPal connection error dismissed, instead of showing it again and asking PayPal for another onboarding link.
- Load PayPal's onboarding script into the editor canvas so the Connect with PayPal button opens PayPal's window instead of a new browser tab.
- Log a notice when stored PayPal credentials cannot be decrypted and are removed, instead of removing them silently.
- Make the Copy Link button work in the payment button's QR code panel, where clicking it previously did nothing.
- Offer Connect with PayPal on WordPress.com and Jetpack-connected sites, instead of only after PayPal is already connected.
- Open PayPal's onboarding window when you click Connect with PayPal, instead of covering the editor with a blank overlay.
- Open PayPal onboarding in a sized window instead of a stray browser tab when PayPal's onboarding script is unavailable.
- Report a PayPal platform configuration problem directly instead of asking the merchant to try again, which could never help.
- Say how many published posts embed a payment link before it is deleted from the admin.
- Send the "Open PayPal Dashboard" link to the sandbox app list when connecting in sandbox, instead of always opening the live one.
- Show that PayPal is disconnected instead of reporting a connected account, and offer a Reconnect button. Disconnecting now says it applies to the whole site.
- Show the option price on the published page when the product options have their own prices.
- Show the payment a duplicated block actually points at, so two blocks sharing one PayPal payment can no longer display different products or prices.
- Status: Detect a site served on any 127.0.0.0/8 loopback address, or on 0.0.0.0, as a local site.
- Stop accepting prices with decimals for Japanese yen, Hungarian forint and New Taiwan dollar, which PayPal rejects, and remove the Indian rupee, which PayPal does not support.
- Stop the block retrying the PayPal onboarding link forever when the request fails.
- Take the displayed price from the option group PayPal is actually pricing.

## 0.4.0 - 2026-04-11
### Added
- IDC: Add revalidation for IDCs. [#46268]

### Changed
- Dependencies: Update lock file to keep root requirements in sync. [#47418]
- Remove header border-bottom from the admin page for a cleaner unified header appearance. [#47313]
- Update dependencies. [#47472]
- Update design of the sidebar upsell. [#47909]
- Update package dependencies. [#46143] [#46456] [#46552] [#46647] [#46785] [#46854] [#47002] [#47021] [#47099] [#47173] [#47300] [#47371] [#47496] [#47505] [#47684] [#47799] [#47825] [#47890] [#47998]

### Removed
- General: Update minimum WordPress version to 6.8. [#46801]

### Fixed
- Admin Page: Restore border on header component. [#47425]
- PayPal Payments Button: Fix escaping issue for stacked payments buttons. [#47761]

## 0.3.2 - 2025-11-20
### Added
- Tested up to WordPress 6.9. [#45571]

### Changed
- Update package dependencies. [#45478] [#45676] [#45756] [#45915] [#45958]

### Fixed
- Jetpack: Remove getIconColor functions for block icons. [#45992]

## 0.3.1 - 2025-10-09
### Changed
- Update package dependencies. [#45173] [#45200] [#45229] [#45298] [#45299] [#45334]
- Update short description for plugin. [#45443]

## 0.3.0 - 2025-09-16
### Changed
- Improve robustness of PayPal Payment Buttons parsing [#45158]
- Remove admin page for PayPal Payment Buttons plugin. [#44712]
- Update package dependencies. [#44677] [#44701] [#44725] [#45027] [#45096]
- Update readme.txt and adds assets for distribution. [#44584]

## 0.2.0 - 2025-07-25
### Added
- Initial release setup and plugin structure. [#44479]
- Integration with paypal-payments package for core functionality. [#44479]
- Working PayPal Payment Button block with availability data. [#44479]
