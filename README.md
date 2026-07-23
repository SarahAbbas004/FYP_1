# TravelGuard AI — Frontend (Flutter)

AI-powered road safety companion for drivers on the Karakoram Highway
(Islamabad → Gilgit). **This package is frontend/UI only** — no backend,
API, database, authentication, or AI model is implemented. All data
(weather, accident hotspots, alerts, journeys) is dummy/sample data found
in `lib/models/app_models.dart`, ready to be swapped for real API calls.

## Getting Started

1. Install Flutter (stable channel, SDK ≥ 3.3.0).
2. From this folder, run:
   ```bash
   flutter pub get
   flutter run
   ```
3. To build a release APK:
   ```bash
   flutter build apk --release
   ```

## Project Structure

```
lib/
  main.dart                     Entry point, launches SplashScreen
  theme/
    app_theme.dart              Colors, gradients, shadows, Material 3 ThemeData
  models/
    app_models.dart             Dummy data models: hotspots, weather, alerts, journeys
  widgets/                      Reusable UI components
    gradient_button.dart        Gradient CTA button with ripple
    weather_card.dart           Hero weather card + forecast tile
    alert_and_accident_cards.dart  Risk badge, hotspot card, animated alert card
    nav_and_buttons.dart        Bottom nav bar, quick-action buttons, pulsing SOS button
  screens/
    splash_screen.dart
    onboarding_screen.dart      3-page onboarding with skip/next/get started
    login_screen.dart
    register_screen.dart
    home_shell.dart             Bottom-nav shell wrapping the 5 main tabs
    home_dashboard_screen.dart  Main dashboard (weather, quick actions, AI tip, alerts)
    live_route_screen.dart      Map-style route view with custom-painted markers
    hotspots_screen.dart        Historical accident hotspots list
    weather_screen.dart         Hourly + 3-day forecast, AI recommendation
    live_alert_screen.dart      Animated warning cards, dismiss/emergency-call
    emergency_screen.dart       SOS button, GPS, share location, emergency numbers
    travel_history_screen.dart  Past journey cards
    profile_screen.dart         Driver profile, vehicle info, menu
    settings_screen.dart        Notifications, dark mode, language, about
```

## Design System

| Token | Value |
|---|---|
| Dark Blue | `#0B3C5D` |
| Green | `#2E8B57` |
| Background | `#F5F7F9` |
| Danger / Red risk | `#E94B3C` |
| Warning / Orange risk | `#F5A623` |

Material 3, rounded corners (12–32px), soft shadows, and gradient
surfaces are used throughout. Fonts are set via `google_fonts`
(Plus Jakarta Sans).

## Notes for wiring up the backend later

- Replace lists in `lib/models/app_models.dart` with API-fetched data.
- `LiveRouteScreen` currently draws a stylized route with `CustomPainter`
  in place of a real map SDK (e.g. `google_maps_flutter`) — swap in a
  real map widget and keep the same marker/bottom-sheet UI.
- `EmergencyScreen`'s SOS button and call buttons are UI-only; hook up
  `url_launcher` (tel:) and real GPS (e.g. `geolocator`) when ready.
- Login/Register screens do not perform real authentication — they
  navigate directly to `HomeShell` for demo purposes.
