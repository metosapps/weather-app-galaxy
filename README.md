# Weather App for Galaxy

Public website, Privacy Policy, Terms of Use and package-specific advertising configuration for `rad.galxy.weatherslive.accu.gpsweather.dailyapps.channels`.

- Website: https://metosapps.github.io/weather-app-galaxy/
- Privacy: https://metosapps.github.io/weather-app-galaxy/privacy.html
- Terms: https://metosapps.github.io/weather-app-galaxy/terms.html
- Galaxy Store: https://galaxystore.samsung.com/detail/rad.galxy.weatherslive.accu.gpsweather.dailyapps.channels
- Support: izabelastrzelczyk726@gmail.com
- App configuration endpoint: https://raw.githubusercontent.com/metosapps/weather-app-galaxy/main/config/ads.json

## Advertising controls

Edit `config/ads.json` on the `main` branch and **increase `revision`** for every change, including a rollback. Keep the package, store and schema identifiers unchanged.

| Field | Effect |
| --- | --- |
| `ads.enabled` | Master switch for all supported ad formats. Set `false` to disable them. |
| `ads.banner.enabled` | Banner placement switch. |
| `ads.native.enabled` | Native placement switch. |
| `ads.interstitial.enabled` | Interstitial placement switch; the existing cancellable Showing ads notice remains. |
| `ads.appOpen.enabled` | App-open placement switch. |
| `minIntervalSeconds` | Minimum fullscreen cadence, bounded by the app to 60–3600 seconds; initial value 120. Existing stricter eligibility rules still apply. |
| `unitId` | Official Google demo unit for the corresponding format. The current test build rejects other IDs. |
| `links` | Package-specific website, legal, support and store links. Only the app's permitted destinations are accepted. Bundled defaults remain available. |

This configuration is consumed by the updated **1.0.8-samsung-testads** APK. Publishing the file does not retrofit an older installed or store APK; that version must be updated through the normal app distribution process.

The current APK is deliberately limited to **Google Test Ads**. Setting a real publisher unit in this file does not enable production advertising. Production requires a reviewed app build with the exact package's verified IDs and explicit publisher approval. Do not put credentials, signing files, receipts, API secrets or personal user data in this public repository.

Remote settings cannot bypass Premium ownership, advertising-consent eligibility, lifecycle checks, the interstitial notice or the compiled cadence floor. They cannot replace SDKs, install code or change the manifest AdMob App ID. Weather-related Firebase settings remain part of the existing app; GitHub is an additional authoritative advertising kill switch, so an existing disabled placement stays disabled.

The app fetches over HTTPS with bounded timeouts and response size, validates the schema/package/store/revision, and caches the last accepted configuration for at most 24 hours. Without a valid configuration ads stay disabled. Invalid responses do not replace a still-valid cache. After expiration the app fails closed for advertising while weather remains usable. Changes take effect after the device retrieves the update; GitHub/CDN caches and offline devices prevent an instantaneous global kill. Accepted changes discard pending and cached placements. A fullscreen ad already being displayed is left to the SDK's normal dismissal flow.

## Website maintenance

This is a static site with no build dependency, tracking scripts, analytics or contact form. GitHub Pages publishes the root of `main`. Update the legal pages when data practices or available products change, and include the corresponding offline copies in the next APK. The contact email is specific to this app.

The Samsung Galaxy Store badge is an unaltered official asset. Samsung and Galaxy Store are Samsung Electronics trademarks. App artwork and preview belong to the app; third-party trademarks retain their respective rights.

The site does not assert that new in-app purchase products are registered or available. Galaxy Store displays actual availability, pricing and trial eligibility at checkout.
