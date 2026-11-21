# SMS Bridge (Android 11)

A sideloadable Android SMS-to-Telegram bridge for Samsung Galaxy Tab Active Pro.

## Build
1. Open this folder in Android Studio (Hedgehog or newer recommended).
2. Allow Gradle sync/download.
3. Build > Build APK(s), then install the APK on the tablet.

## Setup
1. In Telegram, open @BotFather, run /newbot and create a bot. Copy the token.
2. Open your new bot and send /start.
3. Open SMS Bridge, enter token, tap Eşleştir. The app reads getUpdates and detects your chat ID.
4. Tap Test.
5. Grant SMS permission.
6. Save settings, then tap Aktarımı değiştir to activate.
7. For reliable operation, on Samsung: Settings > Apps > SMS Bridge > Battery > Unrestricted. Also allow background activity and exclude from Sleeping apps / Deep sleeping apps. Keep notification permission enabled if the OS asks.

## Filtering
- Allowed senders: comma-separated fragments. Empty means all senders.
- Keywords: comma-separated keywords.
- Keyword-only mode: when enabled and keywords are configured, only matching SMS bodies are forwarded.

## Security
Bot token is stored locally in SharedPreferences. Anyone with access to the tablet/app data can potentially access it. Telegram receives the SMS text, so avoid forwarding sensitive messages unless necessary. The app does not delete SMS from the tablet.

## Notes
This is a first build scaffold. Test with non-sensitive SMS first. SMS receiver uses Android's SMS_RECEIVED broadcast and requires RECEIVE_SMS. WorkManager retries transient delivery failures.

## In-app guided setup (updated)
- Token guide dialog explains BotFather creation steps and offers a BotFather deep link.
- Token field is masked and has a show/hide control.
- Battery optimization status is checked in-app; button can request exemption and open Samsung app settings.
- Samsung-specific guide explains Unrestricted battery and Sleeping/Deep sleeping apps lists.
