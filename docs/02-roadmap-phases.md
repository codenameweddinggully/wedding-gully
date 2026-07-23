# Wedding Gully — Phased Roadmap (v2)

Companion to [01-vision-and-strategy.md](01-vision-and-strategy.md). No fixed deadlines by design — each phase has an exit criterion instead of a date. Move to the next phase only when the current one's exit criterion is genuinely true.

Website/invitations has been removed from this roadmap entirely (not deferred) — that's LetsAnnounce's product, not ours.

---

## Phase 0 — Foundation

Repo, architecture, and local dev environment. No user-facing features yet.

**Deliverables**
- Monorepo structure: `apps/`, `packages/`, `docs/`, `knowledge/`, `prompts/`, `scripts/`, `assets/`
- Next.js + TypeScript app scaffold (deployed to Vercel)
- FastAPI backend scaffold
- Docker Compose for local development
- Dedicated Supabase project connected (Auth + DB + Storage)
- Database schema v1: `users`, `vendor_profiles`, `categories`, `listings`, `media`, `inquiries`, `saved_vendors`, `admin_roles`
- Admin panel scaffold with a **Settings module** (category/city management, roles & permissions from day one — not bolted on later)
- Engineering docs: API design doc, DB schema doc, folder/naming conventions

**Exit criteria:** Next.js ↔ FastAPI ↔ Supabase running end-to-end locally via Docker. Empty but functional skeleton.

---

## Phase 1 — MVP Marketplace (Bangalore, Photographers & Videographers)

The core wedge, launched as narrow as possible on purpose.

**Deliverables**
- Vendor listing pages (boutique-style: photos, description, pricing hints, location)
- Browse/search/filter by price/budget within the single launch category and city
- **Guided discovery wizard**: rule-based quiz (what are you looking for, budget, date, style) that filters/ranks results
- Inquiry/lead capture form (couple → vendor) — no live payments
- **Payment flow UI mockup only** — the escrow flow is visually present (so it can be demoed and stress-tested for UX) but moves no real money; see Phase 3
- Saved-vendors dashboard for couples (favorites + private notes/quotes)
- Admin panel: manual vendor onboarding/editing
- Basic couple accounts
- Manual onboarding of first ~20-50 Bangalore photographers/videographers, founder-led concierge
- Lightweight vendor agreement in place before real vendor data goes live

**Exit criteria:** A real couple in Bangalore can use the guided wizard, browse real photographers, and send a real inquiry; a real vendor receives and can respond to it.

---

## Phase 2 — Trust Layer

Turns "Trust Guarantee" from a slogan into a mechanism.

**Deliverables**
- Vendor verification workflow against the starter checklist: portfolio proof, ID/business verification, founder portfolio review, signed vendor agreement, response-time commitment
- Trust Guarantee badge + published criteria (TheKnot's "Best of Weddings" badge is the closest reference point — a visible earned mark, not just a star rating)
- Lightweight reviews/ratings
- Admin tooling for quality control and reporting bad actors

**Exit criteria:** Trust Guarantee is a defensible, visible claim backed by an actual process.

---

## Phase 3 — Real Escrow Payments

Replaces the Phase 1 mockup with actual money movement, once there's a trustworthy vendor base to move money toward.

**Deliverables**
- Integration with a licensed payment aggregator / escrow-as-a-service partner (e.g. Razorpay Route, Cashfree) — **not** in-house fund custody, for RBI compliance reasons
- Vendor KYC/bank verification as part of onboarding
- Approval-stage state machine: paid → held → work in progress → delivered → approved/disputed → released/refunded/partial
- Dispute mediation workflow in the admin panel, with full record-keeping of every stage
- Applies uniformly to every vendor category and every vendor, including LetsAnnounce — no exceptions

**Exit criteria:** A real transaction flows couple → platform → vendor, including at least one handled dispute, with a complete audit trail.

---

## Phase 4 — AI Wedding Consultant

Only once there's real vendor data and real inquiry/booking behavior to recommend from.

**Deliverables**
- Conversational assistant that recommends vendors based on budget, style, location, date — upgrading the Phase 1 rule-based guided wizard rather than replacing it with something unrelated
- Surfaces inquiries directly from the AI conversation

**Exit criteria:** AI consultant measurably increases inquiry conversion versus the rule-based wizard alone.

---

## Phase 5 — Guest Management + Planning Tools

**Scope genuinely undecided as of this writing** — flagged as an open question for the CEO (see [03-founder-requirements.md](03-founder-requirements.md)): is this Wedding Gully's territory, or does LetsAnnounce want to grow into it? Don't start building until that's resolved.

**Likely deliverables, if in scope**
- Guest list + RSVP tracking
- Budget and planning checklists
- Notifications (email / SMS / WhatsApp reminders)

---

## Phase 6 — Monetization, Shared Ecosystem, and Scale

**Deliverables**
- Formalize monetization: commission, lead-gen fees, escrow transaction fee, or vendor subscription/premium placement — shaped by real Phase 1-4 usage data, not guessed upfront
- **Shared login (SSO) between Wedding Gully and LetsAnnounce** — the "one ecosystem" integration, deliberately built here once both products have real usage to justify it
- Analytics, CMS for content/SEO
- Expansion beyond Bangalore/Photographers into the rest of the category taxonomy and other cities
- Architecture audit for multi-currency/multi-region before expanding outside India

---

## Sequencing notes

- Do not start Phase 4 (AI Consultant) before Phase 1-2 have real vendor data — an AI consultant with no data is a generic chatbot wrapper, undermining the "AI-first" claim rather than proving it.
- Do not attempt in-house payment custody at any phase — always via a licensed partner (Phase 3).
- Do not start Phase 5 without an explicit answer from the CEO on scope.
- Do not start Phase 6 monetization design from a blank slate — let Phase 1-4 usage shape it.
