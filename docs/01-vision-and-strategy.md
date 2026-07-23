# Wedding Gully — Vision & Strategy (v2)

Status: Founding ideation, in progress. Codename only — brand name TBD, decided later (see Team & Company below).

## What we're building

An AI-first, premium wedding **vendor marketplace**, built for India first with global-ready architecture. Not a wedding website/invitations product — that space is explicitly owned by our partner company, LetsAnnounce (see below).

Long-term vision: vendor marketplace, AI Wedding Consultant, guest management, and planning tools. Website/invitations is permanently out of scope for this product — not deferred, excluded.

## Team & company structure

Two-person partnership, not a solo venture:
- **CEO:** owns LetsAnnounce (letsannounce.com), a digital wedding invitation studio — video invites, e-cards, save-the-dates, plus a free bundled "Wed-Page" webpage on larger orders. Proposed the marketplace idea.
- **CTO:** the user, builds with an AI-assisted workflow (ChatGPT for architecture/product, Claude Code for development, browser for UI review — no Figma). Has product/technical decision authority delegated from the CEO.

Not incorporated yet. The plan is to prove the product works before formalizing the company, buying a domain, or locking a final brand name. "Wedding Gully" is a working codename the CEO likes and the CTO is lukewarm on — not a brand decision yet.

## Relationship with LetsAnnounce

Two separate, collaborating companies, not one product with two features:
- LetsAnnounce keeps running its own invitation business independently.
- LetsAnnounce is listed as a vetted **vendor** inside the Wedding Gully marketplace (category: Invitations & Stationery) — the "boutique studio" option for couples wanting unique/custom invitation work.
- Wedding Gully refers couples needing custom premium invitation work to LetsAnnounce.
- **Shared login (SSO) across both products is the agreed long-term direction** — "should feel like one ecosystem" — but it's explicitly a later-stage build (Phase 6), not a Phase 0-1 architecture requirement. Early architecture should avoid decisions that would make this hard later, without building it now.
- LetsAnnounce goes through the **same** vendor rules as every other vendor on the marketplace, including the payment/escrow flow once that's live — no special-casing, per explicit founder decision.

## Why marketplace first

- Most differentiated and monetizable long-term (commission / lead-gen / premium placement / escrow fee).
- Establishes **Trust Guarantee** as the core value proposition before anything else builds on top of it.
- Everything else compounds on top of it: AI Consultant needs real vendor data to be useful; guest/planning tools deepen engagement once couples are anchored to the platform.

## The cold-start risk (flagged explicitly)

A two-sided marketplace is empty and useless without both supply (vendors) and demand (couples) present together. Mitigation:
- **Go narrow.** Launch in one city (Bangalore, see [02-roadmap-phases.md](02-roadmap-phases.md)), one category (Photographers & Videographers) — not all-India, all-category.
- **Concierge onboarding, not self-serve.** Founders manually recruit and vet the first ~20-50 vendors before opening signups.
- **Trust Guarantee earned before claimed** — the badge only goes live once a real vetting process backs it.
- **Seed demand from owned channels** — personal network, wedding forums/communities, targeted content, not paid ads, for the first cohort.

## Core product features (confirmed scope, not exhaustive)

- **Vendor marketplace**: browse/search/filter by category, city, price/budget.
- **Guided discovery ("greeting") wizard**: a short onboarding flow — what are you looking for, budget, city, date, style — that filters/ranks results for the couple. Rule-based in Phase 1; becomes the seed for the Phase 3 AI Wedding Consultant. Validated pattern (TheKnot calls theirs a "personalization quiz").
- **Trust Guarantee**: a visible, earned badge backed by a real vetting checklist (see 03-founder-requirements.md), not a star-rating gimmick. Inspired by TheKnot's "Best of Weddings" badges.
- **Saved-vendors dashboard**: couples save vendors with private notes/quotes (TheKnot calls theirs "Vendor Manager"). Cheap to build, strong retention hook.
- **Inquiries/leads**: couple → vendor contact, no payment required to inquire.
- **Escrow payment system** (confirmed core feature, deliberately sequenced): Wedding Gully always sits as payment middleman — couple pays the platform, funds are held, released to the vendor once the couple approves the completed work, with dispute mediation and partial/full refund support, and full approval-stage records. Applies uniformly to **every** vendor category, including large-ticket ones (venues) and including LetsAnnounce. **CTO flag:** this pattern (collect now, settle later, on behalf of a third party) makes Wedding Gully a payment aggregator under RBI rules in India — the plan is to integrate a licensed PA/escrow-as-a-service partner (e.g. Razorpay Route, Cashfree) rather than build in-house fund custody. Phase 1 ships a **UI mockup only** (no live money movement); full implementation is a dedicated later phase.
- **Admin panel with a Settings module**: not just vendor CRUD. Covers category/city management, Trust Guarantee criteria, roles & permissions, notification templates, and later payment/escrow provider config. Grows across phases rather than being a one-off build.

## Target users (v1)

- **Primary:** couples planning weddings in India, urban/premium segment, starting in Bangalore.
- **Secondary:** vendors seeking qualified, high-intent leads — starting with photographers/videographers.

## Monetization

Deferred by design — not locked in before real vendor supply and demand-side usage exist. The escrow payment layer (once built) naturally opens a lead-gen/commission/escrow-fee path. Revisit formally at Phase 6 with real usage data, not before.

## Tech stack (confirmed)

- Frontend: Next.js + TypeScript, deployed on Vercel
- Backend: FastAPI
- Database / Auth / Storage: Supabase
- Docker for local development
- Dedicated Gmail, GitHub, Supabase, and Vercel accounts — kept separate from personal accounts
- No Figma — visual design happens as coded mockups reviewed live in browser; Fable is used as the design-focused subagent for page/visual design work, Claude Code for the real implementation
- Documentation-first, modular architecture, feature-based folders, vendor lock-in minimized

## Non-goals for now

- No wedding website/invitations builder — permanently LetsAnnounce's territory, not a future phase for us.
- No live/functional escrow payments in Phase 1 — mockup UI only.
- No physical products.
- No multi-city or multi-category expansion until the Bangalore/Photographers launch proves out.

## Genuinely open — needs CEO input

- Whether guest management + planning tools are in Wedding Gully's scope, or something LetsAnnounce wants to grow into later. See [03-founder-requirements.md](03-founder-requirements.md) for the full running list of items to take to the CEO.

## Timeline philosophy

No fixed deadline. Priority is getting the architecture and the trust mechanics right over shipping fast — a deliberate founder call, not a default.
