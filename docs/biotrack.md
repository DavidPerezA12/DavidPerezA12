# BioTrack

BioTrack is my main health-tracking project. It started as an iOS app; the work now is keeping the same data and flows usable across iOS, Android and web without letting sync become the whole product.

The iOS app is the furthest along: SwiftUI, HealthKit, Supabase, offline queues, meal logging, recovery, workout sessions and a large test suite. The Android and web versions are catching up around the same data model.

## What Exists

- Five main areas: summary, activity, diet, recovery and profile.
- Workout sessions with routines, exercise ordering, rest handling, drafts, persistence and HealthKit export.
- Nutrition logging with manual entry, barcode normalization, OpenFoodFacts lookup and nutrition-label OCR/vision fallback.
- Recovery work around sleep, HRV-style signals, manual sleep sessions and recovery score calculation.
- Supabase auth/sync with offline queue handling, realtime updates, RLS checks and local-first behavior.
- HealthKit integration split into smaller services instead of one giant manager.
- Localization resources for English, Spanish, French and German.

The iOS repo has about 559 app Swift files, 116 Swift test files and more than 1,100 `test*` methods. Most of the recent work is around making workouts, sync and recovery less fragile.

## Current Shape

BioTrack is still private alpha. It is broad enough to use as a real tracker, but I would not call it finished. The hard parts are not the screens; they are the parts that decide whether the app feels trustworthy:

- keeping an active workout stable when the app backgrounds;
- reconciling local edits with remote Supabase state;
- keeping HealthKit/Health Connect data useful without duplicating or corrupting it;
- making recovery and nutrition data explainable instead of just decorative.

Recent local work has focused on workout-session stability, recovery, Supabase repositories, sync coverage and test expansion.

## Why I Keep Building It

Most fitness apps split the day into separate silos: gym app, food app, Apple Health, notes, spreadsheet, sleep app. BioTrack is my attempt to keep those signals in one practical place, with native integrations where they matter and enough offline behavior that the app does not feel dependent on perfect network conditions.
