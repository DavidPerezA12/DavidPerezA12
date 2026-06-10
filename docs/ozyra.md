# Ozyra

Ozyra is my personal AI workspace. There are two related codebases: the web app, where most of the work lives, and a native iOS app that ports the same ideas into SwiftUI.

## OzyraChat Web

The web version is a local-first Next.js app. Chats, messages, artifacts, notebooks, notebook documents and image generations live first in IndexedDB through Dexie, then sync to Supabase for auth, backup, quotas, billing, realtime and remote history.

The web app includes:

- streaming chat through `/api/chat`;
- model routing with Ozyra Auto aliases (`ozyra/auto`, `ozyra/auto-eco`, `ozyra/auto-max`);
- BYOK support for OpenAI, Anthropic, Google, GitHub, GitHub Copilot and Tavily;
- notebooks with RAG, document context and overview generation;
- Image Studio plus quick image generation;
- Stripe billing, server-side quotas and usage points;
- `next-intl` localization work across 56 locales;
- tests around sync, IndexedDB behavior and core app logic.

The app is not just a chat skin. A lot of the work is in the plumbing: local schema migrations, cross-tab sync, encrypted provider keys, quota accounting and keeping notebook/image flows attached to the right chat context.

## OzyraApp

OzyraApp is the native iPhone/iPad companion. It is not a web wrapper. It uses SwiftUI, URLSession streaming, a native model selector and Keychain-backed secrets. The web repo remains the source of truth for Supabase migrations, model data and API contracts.

The iOS catalog ports Ozyra's model setup into Swift. The documented catalog covers Ozyra Auto aliases, OpenRouter primary/small/legacy models, image models, GitHub Models, GitHub Copilot, OpenAI, Google and Anthropic entries. The visible iOS selector focuses on Auto, primary and small models for now.

## Status

Private alpha. OzyraChat has the deeper feature set. OzyraApp is the native experiment: same model catalog and chat contracts, but with iOS storage, streaming and UI choices instead of a wrapped web app.
