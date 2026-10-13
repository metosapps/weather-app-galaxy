# Weather App for Galaxy

Public website, Privacy Policy, Terms of Use and package-specific advertising configuration for `rad.galxy.weatherslive.accu.gpsweather.dailyapps.channels`.

- Website: https://metosapps.github.io/weather-app-galaxy/
- Privacy: https://metosapps.github.io/weather-app-galaxy/privacy.html
- Terms: https://metosapps.github.io/weather-app-galaxy/terms.html
- Galaxy Store: https://galaxystore.samsung.com/detail/rad.galxy.weatherslive.accu.gpsweather.dailyapps.channels
- Support: izabelastrzelczyk726@gmail.com
- Release configuration (1.0.9+): https://raw.githubusercontent.com/metosapps/weather-app-galaxy/main/config/ads-release.json
- Legacy test configuration (1.0.8): https://raw.githubusercontent.com/metosapps/weather-app-galaxy/main/config/ads.json

## Advertising controls

All advertising is currently disabled: the global switch and all four format switches are `false`. Keep them disabled until the exact update is live and the publisher explicitly authorizes activation. There is no scheduled or automatic activation.

For **1.0.9+**, edit `config/ads-release.json` on `main` and **increase `revision`** for every change, including a rollback. Keep `ads.mode` equal to `production`, and keep the package, store, schema and exact unit IDs unchanged. A later activation requires both the master switch and the desired format switches. Consent, Premium and lifecycle checks still apply.

Keep legacy `config/ads.json` disabled. It is a separate kill switch for the earlier 1.0.8 test APK; enabling the release config must never re-enable old test builds.

| Field | Effect |
| --- | --- |
| `ads.enabled` | Master switch for all supported ad formats. Set `false` to disable them. |
| `ads.banner.enabled` | Banner placement switch. |
| `ads.native.enabled` | Native placement switch. |
| `ads.interstitial.enabled` | Interstitial placement switch; the existing cancellable Showing ads notice remains. |
| `ads.appOpen.enabled` | App-open placement switch. |
| `minIntervalSeconds` | Minimum fullscreen cadence, bounded by the app to 60–3600 seconds; initial value 120. Existing stricter eligibility rules still apply. |
| `unitId` | Exact compiled production unit for this app and format. Other units and test mode are rejected by the release APK. |
| `links` | Package-specific website, legal, support and store links. Only the app's permitted destinations are accepted. Bundled defaults remain available. |

The release configuration is consumed by **1.0.9** (version code 10). It uses a new cache namespace and requires production mode, so an enabled test configuration cached by 1.0.8 cannot turn on real ads after upgrade. The default, unavailable-config and expired-cache behaviors all keep ads disabled. Ads disabled also blocks the app's explicit Mobile Ads initialization path.

The app-specific AdMob App ID is `ca-app-pub-3289974964220873~8616823829`. Compiled units are:

| Format | Production unit ID |
| --- | --- |
| Banner | `ca-app-pub-3289974964220873/9357576220` |
| Native | `ca-app-pub-3289974964220873/2501532997` |
| Interstitial | `ca-app-pub-3289974964220873/3814614667` |
| App open | `ca-app-pub-3289974964220873/8044494559` |

The publisher provided these identifiers for this app. Configuration/build verification is not proof of production ad fill or AdMob policy clearance. Publishing these files does not retrofit the original app: users must receive a build which consumes remote configuration. Earlier 1.0.8 test installations also need to fetch the disabled legacy config; an offline enabled cache can remain valid for up to 24 hours. Do not put credentials, signing files, receipts, API secrets or personal data in this public repository.

Remote settings cannot bypass Premium ownership, advertising-consent eligibility, lifecycle checks, the interstitial notice or the compiled cadence floor. They cannot replace SDKs, install code or change the manifest AdMob App ID. Weather-related Firebase settings remain part of the existing app; GitHub is an additional authoritative advertising kill switch, so an existing disabled placement stays disabled.

The app fetches over HTTPS with bounded timeouts and response size, validates the schema/package/store/revision, and caches the last accepted configuration for at most 24 hours. Without a valid configuration ads stay disabled. Invalid responses do not replace a still-valid cache. After expiration the app fails closed for advertising while weather remains usable. Changes take effect after the device retrieves the update; GitHub/CDN caches and offline devices prevent an instantaneous global kill. Accepted changes discard pending and cached placements. A fullscreen ad already being displayed is left to the SDK's normal dismissal flow.

## Website maintenance

This is a static site with no build dependency, tracking scripts, analytics or contact form. GitHub Pages publishes the root of `main`. Update the legal pages when data practices or available products change, and include the corresponding offline copies in the next APK. The contact email is specific to this app.

The Samsung Galaxy Store badge is an unaltered official asset. Samsung and Galaxy Store are Samsung Electronics trademarks. App artwork and preview belong to the app; third-party trademarks retain their respective rights.

The site does not assert that new in-app purchase products are registered or available. Galaxy Store displays actual availability, pricing and trial eligibility at checkout.
