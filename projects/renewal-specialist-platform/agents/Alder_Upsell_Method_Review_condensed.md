# Alder's Upsell Analysis Method — Condensed Review (PII-free)

*Derived from the full v2 review (Alder's 2026-09-29 decisions applied and preserved exactly); for Alder's review only. Tags: [F] fact · [I] Alder's interpretation · [H] hypothesis · TS = [TIME-SENSITIVE — verify]. Meetings M01–M16, sellers S1–S12 (§2). "Alder" = Copilot/AI direction; SS = security specialist (security, migration, assessments); "partner" = partner or reseller; CfS = Copilot for Security.*

## 1. Executive summary

**Evidence limits [F].** 72 calendar entries; 17 transcripts, all from one 14–29 Sep 2026 window; 44 earlier sessions lapsed retention. This shows how Alder worked in late September, not how the method evolved.

1. **Stable sequence:** frame (renewal timing ∥ segment; then channel, partner/contact status, CRM hygiene) → Copilot read (purchased → assigned → active) → licence inventory → security telemetry with usage-ratio test → data/Power BI white space → on-prem/Azure → rank 2–4 talk tracks with owner, resource, documentation. Eligibility (§9.1) checked during the footprint read.
2. **Adoption before expansion** — default expectation, not hard rule: idle seats demote expansion (M02, M03, M04, M13, M15, M16); unused A5 features shelve A5 (M04, M06, M09, M11, M12); ≈90%+ adoption makes Copilot the lead (M05, M08, M10, M12). Conversation overrides either way.
3. **Security is the foundation for AI:** A3 + Copilot present/planned → security leads (M01, M10, M13, M16); A5 + Sentinel used → security closed (M05, M07, M08, M12, M15). A3 + high adoption → both tracks; open with security when unsure. Not a hard prerequisite for a curated-data pilot.
4. **Segment shifts probabilities, not rules:** K-12 → minors'-data compliance, IT workload, Copilot for admins (innovation plays lower-prior); Higher Ed → research, agents, Azure AI, Fabric, GitHub Copilot (tendencies).
5. **"No recommendation yet" is legitimate** (M04, M11, M16); hypotheses travel "up the sleeve".
6. **Attribution doctrine:** near-renewal finds = top-growth children; proof = child + relevant documentation; partner before customer; specialist "on the bus" early, high level.
7. **Open verifications:** a handful of licensing mappings and unsourced statistics (§10); eligibility fixed by §9.1.

**Bottom line:** encode the sequence, repeated heuristics and eligibility table with high confidence; treat remaining licensing claims as parameters to verify; never generalise single-account arithmetic.

## 2. Evidence base

| Item | Value |
|---|---|
| Calendar entries (29 Apr–29 Sep 2026) | 72 |
| Expired (Apr–Jul; ~60-day retention) | 44 — contents must not be inferred |
| In-window untranscribed / cancelled / not yet held | 7 / 2 / 2 |
| Transcribed | 17 — 16 usable; 1 one-minute process clip excluded |
| Window | 14–29 Sep 2026 only |
| Segment mix (usable) | 10 Higher Ed · 5 K-12 · 1 nonprofit (out of scope; evidence only) — US/Canada |
| Sellers in usable sessions | 12 (S1–S12); seller audio unusable in ≥5 sessions — substance is Alder's |
| Customer-meeting outcomes | None observed — no hypothesis validated |

| Key | Date / time | Seller | Key | Date / time | Seller |
|---|---|---|---|---|---|
| M01 | 2026-09-14 11:30 | S1 | M09 | 2026-09-17 13:30 | S6 |
| M02 | 2026-09-15 11:00 | S2 | M10 | 2026-09-18 11:00 | S7 |
| M03 | 2026-09-15 11:30 | S3 | M11 | 2026-09-18 11:45 | S8 |
| M04 | 2026-09-15 14:30 | S2 | M12 | 2026-09-21 15:00 | S8 |
| M05 | 2026-09-16 10:45 | S1 | M13 | 2026-09-23 13:30 | S9 |
| M06 | 2026-09-16 14:00 | S4 | M14 | 2026-09-25 11:30 | S10 (out of scope) |
| M07 | 2026-09-16 14:45 | S5 | M15 | 2026-09-28 10:30 | S11 |
| M08 | 2026-09-17 11:45 | S3 | M16 | 2026-09-29 11:30 | S12 |

Excluded clip: 2026-09-23 11:30, S2 — masterclass nomination recorded against a child opportunity (weak indicator only). Institutions, acronyms, partners, locations and account figures removed; footprints described qualitatively.

## 3. Meeting-by-meeting (compact)

| Key | Segment | Footprint pattern | Lead recommendation(s) | Rejected / deferred | Next action & owner role | Confidence |
|---|---|---|---|---|---|---|
| M01 | Higher Ed | Well-used A3; small Copilot pilot mostly active; Defender, free XDR, Purview, heavy Entra; Sentinel near-zero; substantial on-prem. [I] security signals > AI | Security on A3: paid XDR, Entra Identity Lifecycle, Purview DLM (TS mapping); pilot-to-production via open question; broad AI discovery; migration "why" | Copilot expansion lead; security as hard prerequisite; Entra P2 as vehicle (TS); Sentinel pitch | Seller: baseline discovery → AI if solid; blockers → partner; enablement → masterclass (§9.1); expansion → Alder; migration → SS | Moderate (security); Exploratory (rest) |
| M02 | Higher Ed | Largest deal, near renewal; large Copilot base, large idle share, assigned seats well used; large A5; XDR; Sentinel near-zero. [H] lead may not be Copilot | Fill unassigned seats; AI-journey discovery → Alder; Sentinel as workload reduction (TS attribution); flag Dynamics grace-period anomaly; partner first | Seat expansion; A5 upsell; free-tier → paid; Fabric lead; quoting price | Seller: partner → discovery with Alder → Sentinel/Fabric probes (SS) → CRM flag | Moderate; process High |
| M03 | Higher Ed | Renewal inside the top-growth window; tiny pilot, almost unassigned; A5 fully used, Intune idle; no Sentinel; huge student base vs small team. [I] licence upsell exhausted | Sentinel + CfS first → SS; AI as a whole → Alder; adoption via partner (below masterclass minimum); hybrid "why" + TCO; activate Intune; top-growth child with proof | More Copilot now; masterclass; security licence upsell; vague "next year"; children without evidence | Seller: partner → discovery → consultation/assessment → child; monthly partner follow-up; close won/lost | Moderate (Sentinel); High (process) |
| M04 | K-12, two tenants | Renewal imminent; tiny pilot partly used; A3 majority, A5 block unused; minimal security activation; little on-prem. [I] "no strong signals" | Pilot as only path; security pain probe (Sentinel/CfS only on pain); ask about free-tier users; low-commitment discovery; limit effort | A3→A5 (seller idea); security upsell; Copilot as strong play; migration | Seller: discovery + follow-up; check renewing tenant, currency vs book | High (low potential); Exploratory (products) |
| M05 | Higher Ed (inferred), CSP | Auto-renewing; established Copilot base grown in tranches, near-full active; A5 + Sentinel heavy; Power BI Pro, no Fabric; book vs invoice mismatch. [I] strong adoption; security "closed" | Expand Copilot (Frontier framing); Fabric via need questions; Security Copilot only if in-house SOC; university AI use cases; renewal as pretext; escalate mismatch (TS CSP invoicing) | Dynamics-renewal lead; broad security upsell; product-named questions; assessments as guaranteed; buying seats to qualify (TS) | Seller + Alder: needs discovery → Copilot scale → Fabric → conditional Security Copilot; mismatch to manager | High (Copilot); Moderate (Fabric) |
| M06 | K-12, CSP | T-minus ~3; tiny Copilot pilot, fully used; base with targeted add-ons; Entra, Defender for Office, Purview heavy; Intune barely. [H] licensing deliberately optimised | Pilot-to-production → Alder; security pain → SS if need; plan-level P2 add-ons; assessment after discovery (§9.1); contact reseller; booked next step; forecast comments | Top-tier upsell; masterclass (below minimum); Azure AI (lower K-12 prior); immediate assessment; raw seat totals | Seller: need discovery → Alder touch-base → reseller. Alder: CRM comments | Moderate (Copilot); Exploratory (security) |
| M07 | Higher Ed | Top deal via reseller; tiny long-standing pilot fully used; all-A5, Sentinel used, CfS idle; no Fabric; substantial on-prem; customer silent. [I] "biggest space is AI" | AI-centred need discovery; migration + Azure Solution Assessment (>5 VMs) → SS; Copilot expansion; Azure AI; reseller today; customer-ready collateral | Any security upsell; in-renewal sale; Dynamics; masterclass (below minimum); unconfirmed education-specific assessment | Seller: partner (urgent) → AI/on-prem discovery → assessment if >5 VMs → Fabric/CfS low | Moderate (AI/Azure); High (process) |
| M08 | Higher Ed | Very near expiry; mature Copilot footprint ≈90% active; some agent use; no build SKUs; A5 fully used except Sentinel; substantial on-prem. [H] agent-sharing limit ahead (TS) | Grow Copilot to other departments → Alder; masterclass (§9.1); Copilot Studio → Alder scoping; GitHub Copilot for researchers; migration/TCO → SS; Sentinel/CfS only if raised | A3→A5; Dynamics (single connector); Azure architecture selling; in-renewal purchase; product-led Studio pitch | Alder: scale session → masterclass → Studio; SS: migration/TCO; book Alder live | High (Copilot, masterclass); Moderate (Studio, migration) |
| M09 | K-12 | Handed-down, untracked, no forecast comment; A3 + A5 mix; no paid Copilot, many Chat users; fails usage test; many Power BI Pro; negligible on-prem. [I] "doesn't use what it has" | Add Alder to deal team; partner first; finds = top growth; security gap discovery; AI discovery + pilot design (Alder); Fabric via need questions; migration only, TCO if >5 VMs | More A5; broad security pitch; Copilot as sure bet; masterclass (no paid Copilot); Dynamics; customer before partner | Seller: partner → three-scenario discovery → Alder (AI) → Fabric → TCO gate → child on evidence | Exploratory (products); High (process) |
| M10 | Higher Ed, two tenants | High-revenue account near renewal; large Copilot base ≈90% active; all-A3, strong suite use; Power BI Premium; Azure prepayment; substantial on-prem. [I] manual labelling implausible at scale (resolved-rule case) | Copilot expansion; AI beyond Copilot → Alder, partner MVP; masterclass (proactive); A5 for sensitive users / add-ons / Sentinel-XDR / CfS by pain; Fabric; TCO assessment; children with resource; meet customer now | Product-first discovery; Copilot as only topic; "thought about migrating?"; competing on MVP; full-chain attribution; Sentinel as automatic answer | Seller: AI-led then security discovery → Alder (Studio/Foundry) → SS → Fabric → TCO → child + documentation | High (Copilot, A5); Moderate (Fabric, migration) |
| M11 | Higher Ed, CSP | Attribution post-mortem: very large Copilot block bought via reseller before opportunity/contact; under half active; A5 features barely used; customer "already renewed" | Stop pursuing attribution; top-growth attempt only if customer responds; defend renewal metric via base growth; book Alder early on top deals; CSP intro script; child + documentation model | Any Copilot/AI or A5 upsell; competing with partner; claiming via TPID; full prep; POC/quotes | Seller: low-effort email. Alder: document session | High (nothing attributable); Insufficient (forward) |
| M12 | K-12 | Top deal, agreement ending imminently; small pilot grown mid-term, near-full active; A5 + A3 + add-ons; "uses everything, even Sentinel"; Power BI Premium; large Azure prepayment. [I] pilot worked; renewal after 1 Oct → A7 fits | Lead with AI: more Copilot for faculty/admin; masterclass hook (§9.1); Cowork/PAYG (hedged); security as readiness — Purview portal assessment (TS) / Alder / AI-Ready Secure Foundation; consider A7; add-ons only; Fabric second; Azure last | A5 pitch; innovation narrative (Foundry, GitHub Copilot education tier (TS), Studio) — lower prior; Copilot for students; migration push; Sentinel | Seller: AI → Fabric → Azure/add-ons; book Alder ≥1 day ahead; contact customer despite timing | High (Copilot); Moderate (masterclass, readiness, Fabric) |
| M13 | Higher Ed | Near renewal; two TPIDs; partner responsive, customer uncontacted; paid A3; pilot with material unassigned share; small Azure prepayments consuming AI models; large on-prem. [I] "could easily be a pilot"; [H] "building something" | Lead with security: A5 / compliance add-on suite / A7, "scale with confidence", AI-Ready Secure Foundation; pilot-to-production + masterclass (proactive); Azure AI project discovery; migration fallback; partner first; book Alder; fix TPID | Ownerless masterclass offer; bulk Copilot without security; team building the Azure AI deal; renewal-only partner talk; Sentinel as signal | Seller: partner → security → Copilot → Azure AI → migration; Alder: high-level discovery; notes in opportunity | High (order); Moderate (Copilot); Exploratory (Azure AI, migration) |
| M14 | Nonprofit (out of scope) | Education framework reused by analogy; security baseline; no paid Copilot, active Chat | First Copilot seats as small pilot with assessment hook; Alder for pilot design; outreach around resources | — | Evidence only; supports no pattern or rule | — |
| M15 | K-12, multi-institution | Near renewal; A5 deployed at scale; Copilot pilot with adoption gap; students/teachers on Google/Chrome OS. [I] security "no attack surface"; AI for admin staff | Pilot-to-production via masterclass/showcase (§9.1), prove value by adoption and hours saved; partner now; incentives only as "we might have resources"; no security sale; migration lightly; children per area (build vs consumption) | Security/A5 pitch; AI Readiness assessment; Azure AI (lower prior); deep technical consultations; empty pipeline; promising incentives | Seller: partner → discovery with Alder → masterclass → child + documentation. Alder booked only for Copilot-flagged/commented accounts | Moderate (Copilot); High (process) |
| M16 | Higher Ed, multi-tenant | Renewal imminent; partner moving customer to cheaper tier; customer unresponsive; A3 base; established Copilot footprint, poor adoption; many Chat users. [I] "most likely nothing will happen" | Copilot expansion via use cases (agents/Studio, Cowork, next department); masterclass to fix adoption and protect renewal (§9.1); A3→A5 for Copilot users; value-framed partner email on both tracks; recapture freed budget; child per need | Containment plan; pilot-style questions; naming products/seat counts; pursuing customer directly; active investment | Seller: partner email → conditional discovery → masterclass and A5 as resources → child if need | Moderate (both); High (little will happen) |

## 4. Cross-meeting patterns

**Repeated** = ≥4 sessions across segments. M14 never cited. Near-duplicates merged (P-numbers from the full review).

| ID | Pattern | When | Classification | Support |
|---|---|---|---|---|
| P1+P11 | Segment before solution; K-12 → compliance, IT workload, Copilot for admins; Higher Ed → research, agents, Azure AI, Fabric, GitHub Copilot (tendencies) | Every account; parallel first step with timing | Repeated / segment-specific (Alder: tendencies) | 10 — M01, M02, M04, M06, M07, M09, M10, M12, M15, M16 |
| P2+P3 | Timing/channel frame: ≤~3 months (EES) → top growth, effort calibrated; CSP/online auto-renews → discovery-led growth, buy any time; no other channel effect. "T-minus 6" = illustration | Every account | Repeated — parallel first step (Alder) | 10 — M03, M04, M05, M06, M07, M08, M09, M11, M12, M15 |
| P4 | Customer problem before product; never "do you use Fabric?"; seller recognises pattern only | Every discovery | Repeated | 8 — M01, M05, M06, M07, M08, M09, M10, M16 |
| P5 | Signal ≠ confirmed opportunity; hypotheses "up the sleeve"; only the customer validates; forecast comment = hypothesis | Every prep | Repeated | 9 — M02, M03, M06, M09, M10, M11, M13, M15, M16 |
| P6 | Adoption before expansion (purchased → assigned → active); idle seats trigger adoption resources; overridable (fully used tiny pilot → expansion, M07) | Copilot and A5 | Repeated — default, not hard rule (Alder) | 8 — M02, M03, M04, M09, M12, M13, M15, M16 |
| P7+P9 | Use paid capacity first; tier candidate only if ≥3 of 4 security workloads at ≥50% active ÷ licensed (Sentinel excluded; free seats excluded); A3/A5 imbalance alone no signal; "4–5 checks" (M06) superseded | Before any A5/A7 recommendation | Repeated — canonical test confirmed (Alder) | 6 — M03, M04, M06, M09, M11, M12 (+M10 implicit) |
| P8 | Security as foundation for AI: A3 + Copilot → security leads; A5 + Sentinel used → closed; not a hard prerequisite for a curated pilot; A3 + high adoption → both, security first when unsure | Any account scaling AI | Repeated | Leads M01, M10, M13, M16; closed M05, M07, M08, M12, M15 |
| P10 | Security ladder Defender → XDR → Sentinel → CfS; Sentinel framed as workload reduction | Mature Defender use | Solution-specific | 4 — M02, M03, M05, M08 |
| P12 | Copilot label by seat count/date: ≤~25 seats (estimate) → pilot-to-production; larger → scale-and-transform; conversation can move it | Every Copilot review | Repeated — estimate (Alder) | 8 — M01, M02, M03, M06, M07, M08, M10, M13 |
| P13 | Discovery before solution; specialist high level (direction, business case); seller picks no products or seat counts | Every next step | Repeated — depth confirmed (Alder) | 6 — M02, M07, M08, M09, M15, M16 |
| P14 | Partner before customer; ask what they work; partner-originated needs attributable if resource aligned; incentives = partner's | Large/silent/near-renewal accounts | Repeated | 8 — M02, M03, M06, M07, M09, M13, M15, M16 |
| P15 | Eligibility (§9.1) checked during footprint; masterclass proactive when eligible; assessments on confirmed need; nothing guaranteed | Masterclass and assessments | Repeated — proactive posture (Alder) | 8 — M01, M05, M06, M07, M08, M09, M13, M15 |
| P16 | Documentation for attribution: forecast comment; child per need; proof = child + relevant documentation; "get on the bus early" | Every engagement | Repeated — proof standard confirmed (Alder) | 9 — M01, M03, M06, M09, M10, M11, M13, M15, M16 |
| P17 | Every conversation ends with outcome + booked next step; "never get blocked"; no commitments | Every customer/partner meeting | Repeated (small sample) | 3 — M06, M08, M12 |
| P18 | "No recommendation yet" → low-effort follow-up + documentation | Weak/dead/partner-controlled deals | Repeated | 3 — M04, M11, M16 |
| P19 | Test seller's ideas against usage data; rebut or downgrade to a question | Coaching | Repeated | 3 — M02, M04, M07 |
| P20 | Role boundary: no quoting, pricing, POCs, implementing, closing — partner does; team = guidance + resource access | Pricing/delivery topics | Repeated | 5 — M02, M03, M11, M13, M16 |
| P21 | Data hygiene first: both tenants, TPID, deal team, annual vs monthly, committed vs invoiced, currency | Multi-tenant, CSP, cross-border | Repeated | 6 — M04, M05, M06, M09, M13, M16 |
| P22 | Power BI volume → data fragmentation → Fabric | Power BI without Fabric | Solution-specific | 5 — M05, M07, M09, M10, M12 |
| P23 | Server lines → rough VM estimate → migration + TCO only (assessment >5 VMs); architecture expansion out of scope; "on-prem by necessity" (M12) = illustration | Server licences present | Solution-specific | 8 — M01, M03, M07, M08, M09, M10, M12, M13 |
| P24 | Azure prepayments consuming AI models → live project to chase before partner quotes | Higher Ed with Azure AI spend | One-time | 1 — M13 |
| P25 | Free Copilot Chat users → first-seat/expansion signal (may be students) | Zero/few paid seats | Repeated (small sample) | 3 — M09, M16, illustrative in M11 |

## 5. Canonical analysis method

Vs the 13-step hypothesis: hygiene step added; timing and segment are parallel first steps (Alder); partner/contact status read during framing; footprint has a fixed order (Copilot first) with embedded eligibility check; effort calibration explicit.

0. **CRM hygiene** — opportunity/tenant mapping, forecast comment ("no comment = no strategy"), deal team, TPID, tenant count → clean context. (M01, M04, M06, M09, M13)
1. **Frame** — four parallel reads before any product view → buying horizon, effort level, likely themes, first contact: **A** T-minus: in-renewal vs top growth; calibrate effort (M03, M04, M07, M09) · **B** segment: conversation set as tendencies (M01, M09, M15, M16) · **C** agreement/channel: EES/OVS vs CSP/online, annual vs monthly, currency — buying timing only (M04, M05, M06) · **D** partner/contact status: customer reached? partner responsive, knows account? (M07, M09, M13, M15)
2. **Copilot first** — purchased → assigned → active; dates/tranches; agents, Cowork, build SKUs; label pilot (~25 seats, estimate) vs established. (all)
3. **Licence inventory** — base tiers, student benefit, add-ons, Power Platform, Dynamics, Power BI/Fabric, Teams, Entra. (all)
4. **Security telemetry** — per-workload usage; ≥3-of-4 at ≥50% test (Sentinel excluded); Sentinel/CfS presence; Intune. (all in scope)
5. **White space + on-prem** — Power BI without Fabric; server lines → VM estimate; Azure prepayments and what they consume. (M05, M07, M08, M10, M12, M13) · **5b Eligibility check** — minimums vs §9.1 while reading counts; masterclass proactive when eligible. (M05, M06, M07, M08, M12)
6. **Signals → ranked hypotheses** — strength per signal; 2–4 talk tracks; "why now"; A3 + high adoption → both tracks, security first when unsure → ordered tracks. (all)
7. **Reject and test** — reject with usage data; Socratic test of seller ideas; rejected items become questions. (M04, M06, M07, M09)
8. **Discovery questions** — what only customer/partner can answer; need-oriented, never product-named. (all)
9. **Lowest-friction next action** — customer discovery; then book Alder/SS; masterclass proactive; assessments on confirmed need; light email when odds are low. (all)
10. **Routing** — Alder = Copilot/AI/Studio/Foundry direction; SS = security, migration, assessments; partner = quotes, POC, MVP, incentives, closing; floor resource = Dynamics. Involvement high level. (M01, M03, M07, M10, M13, M15)
11. **Documentation** — forecast comment (hypothesis + resources); child per need (build vs consumption) + relevant documentation; monthly partner follow-up; close won/lost. (M03, M10, M15, M16)

Dead accounts still get an abbreviated footprint "so you learn the method" (M11); "take the framework, not the account answer" (M09).

**Recommendation categories (support):** Protect/renew — M05, M11, M16 · Adoption/value realisation — M02, M03, M13, M15, M16 · Pilot definition / first pilot — M09 · Pilot-to-production — M01, M04, M06, M13, M15 · Copilot expansion — M05, M07, M08, M10, M12, M16 · Targeted security discovery — M04, M06, M07, M09 · Security readiness (not sale) — M12, M13 · Security tier/add-on — M01, M06, M10, M13, M16 · Sentinel/CfS exploration — M02, M03, M05, M07, M08 · Copilot Studio/agents — M05, M08, M10, M16 (Higher Ed only; tendency) · Azure AI discovery — M02, M07, M10, M13 (set aside M06, M15) · Fabric/data — M02, M05, M07, M09, M10, M12 · Power Platform — noted only (M02, M09) · Azure migration — M01, M03, M07, M08, M10, M13 · TCO/migration assessment — M03, M07, M08, M09 (gated), M10 · Partner alignment — M02, M06, M07, M09, M13, M15, M16 · Specialist consultation — all usable · Assessment/masterclass — M05, M06, M08, M10, M12, M13, M15, M16 · CRM documentation — M01, M03, M06, M09, M10, M11, M13, M15, M16 · Monitor/follow up — M04, M11, M16 · Insufficient evidence — excluded clip; M02 (free-tier assignment), M12 (migration) · No expansion recommendation — M11, M04.

## 6. Recommendation matrix (by type)

104 account-level rows collapsed to one per type. Confidence: High / Moderate / Exploratory / Insufficient.

| Type | Typical input signal | Interpretation | Validation required | Rejected alternative | Next action | Owner role | Confidence | Meetings |
|---|---|---|---|---|---|---|---|---|
| Security tier/add-on on A3 (paid XDR, Identity Lifecycle, Purview DLM, A5 for sensitive users, compliance suite, A7) | Well-used A3 + Copilot present/planned | Foundation to "scale with confidence" | Customer feels gaps; plan mappings (TS) | Copilot lead; Entra P2 as vehicle | Pain discovery | Seller → SS/Alder | High (order) / Moderate | M01, M10, M13, M16 |
| Plan-level add-ons instead of tier | A3 + targeted add-ons | Licensing already optimised | Capability need | Top-tier upsell | Mention if theme arises | Seller (SS) | Exploratory | M06, M12 |
| Targeted security gap discovery | Weak/uneven activation; K-12 prior | Pain unknown | Recognised gap or incident | Broad pitch; more A5 | Open questions on users, identities, devices, incidents | Seller → SS | Exploratory | M04, M06, M07, M09, M10 |
| Sentinel / CfS (consumption layer) | Defender/XDR used; Sentinel absent or near-zero | Only white space left; workload reduction | In-house SOC; attribution (TS) | Relying on it for revenue | Team-size/console questions; SS assessment | Seller → SS | Moderate / Exploratory | M02, M03, M04, M05, M07, M08, M10 |
| Security readiness, not sale (Purview portal assessment (TS); AI-Ready Secure Foundation) | A5 customer scaling AI | Security = ground, not sale | Blocker confirmed; §9.1 | A5 pitch | Offer if blocker appears | Seller → Alder/SS | Moderate | M12, M13 |
| Activate owned features | Owned SKU unused | Activation, not sale | — | Tier upsell | Mention | Seller | Moderate | M03 |
| Copilot adoption / fill unassigned seats | Large idle share or low activity | Won't buy more until used (default) | Impact; target users; blockers | Seat expansion | Partner/masterclass/Alder for adoption | Seller; partner | Moderate | M02, M03, M13, M15, M16 |
| Copilot pilot-to-production | ≤~25 seats mostly used | Time for touch-base | Goals, users, success criteria | Pitching use cases | Open question → Alder | Seller → Alder | Moderate / Exploratory | M01, M04, M06, M13, M15 |
| Copilot expansion / scale | ≈90%+ adoption or pilot→purchase growth | Value seen → next departments/use cases | Departments; budget; intent | Pilot-style questions | Alder scale session; Frontier framing | Seller → Alder | High / Moderate | M05, M07, M08, M10, M12, M16 |
| First pilot / pilot definition | No paid Copilot; Chat users | Guidance-type blockers | Interest; faculty vs students | Copilot as sure bet | Discovery → Alder pilot design | Seller → Alder | Exploratory | M09 |
| Masterclass nomination | Meets §9.1; adoption gap or growth intent | Unlock deeper use; protect renewal | Eligibility only (proactive) | Below-minimum nomination; ownerless offer | Nominate; tie to child + adoption talk | Seller | High / Moderate | M08, M10, M12, M13, M15, M16 (rejected M01, M03, M06, M07, M09) |
| Cowork / pay-as-you-go | Active users; no PAYG | Next Frontier step | Readiness | Cowork as strong play | Via masterclass/use cases | Seller → Alder | Moderate (hedged) | M12, M16 |
| Copilot Studio / agents | Agents used; student-facing needs | Sharing limit ahead (TS) | Want student/external agents? | Product-led pitch | Use cases → Alder scoping | Seller → Alder | Moderate / Exploratory | M05, M08, M10, M16 |
| GitHub Copilot | University; no build SKUs | Research/dev productivity (tendency) | Dev groups? tier (TS) | K-12 innovation narrative | Explore in discovery | Seller | Exploratory | M08 (M02, M10 mentions) |
| Broad AI-journey / Azure AI discovery | University; Azure spend; AI-model prepayments | "Biggest space is AI" | Projects, stage, blockers | Team building the deal | Alder high-level consultation | Seller → Alder (+partner MVP) | Moderate / Exploratory | M01, M02, M03, M05, M07, M10, M13 |
| Fabric / data discovery | Power BI without Fabric | Fragmented data | Data pain | "Have you used Fabric?" | Need questions → Alder/SS | Seller → Alder/SS | Moderate / Exploratory | M02, M03, M05, M07, M09, M10, M12 |
| Azure migration / TCO + Azure Solution Assessment | Server lines; Azure prepayment | On-prem "for a reason" | Workloads; >5 VMs; intent | Architecture expansion; below-minimum push | "Why hybrid" → SS | Seller → SS (+partner) | Moderate / Exploratory | M01, M03, M07, M08, M09, M10, M12, M13 |
| A7 consideration | Renewal after 1 Oct 2026; A3 + AI | Could fit at renewal | Fit | — | Fold into security lead | Seller | Exploratory | M12, M13 |
| Partner / reseller alignment | Silent customer; no real partner contact | Partner may already be selling | Existing motions; quotes | Customer first | Contact now; ask what they work | Seller | High | M02, M03, M06, M07, M09, M13, M15, M16 |
| Book Alder (high-level discovery) | Copilot-flagged/commented account; accepted meeting | Live support most valuable | Customer acceptance | Blind discoveries | Book ≥1 day ahead; add to deal team | Seller | High | M01, M02, M04, M06, M08, M09, M11, M12, M13, M15 |
| CRM hygiene (forecast comment, deal team, TPID, tenant, currency, committed vs invoiced) | Missing comment; two TPIDs; mismatches | Revenue must land correctly | Tenant mapping | — | Add comments; verify; escalate | Alder / seller | High | M01, M02, M04, M05, M06, M09, M13 |
| Attribution: top-growth child + documentation | Renewal ≤~3 months; identified need | Proof of work needed | Evidence of engagement | Children "out of nowhere"; TPID-only claims | Child per need (build vs consumption) + recap/notes/resource | Seller | High | M03, M09, M10, M11, M12, M15, M16 |
| Effort calibration / follow-up | Weak signals; dead deal; partner-controlled | Little will happen | Customer reply | Heavy investment | Light email; document | Seller | High (posture) | M04, M11, M16 |
| Call reframing / coaching (CSP script, renewal as pretext, needs not products, booked next step, collateral) | CSP auto-renew; product-led habits | Seller = access to Microsoft resources | — | Renewal-only call | Opening script; one-pagers | Seller | High (coaching) | M05, M06, M07, M09, M11 |
| Renewal-metric defence / budget recapture | Lapsing seats vs base growth; freed budget | Redirect narrative or budget | Outcome; intent | Containment plan | Explain in review; raise with partner | Seller | Moderate / Exploratory | M11, M16 |

## 7. "Do not recommend yet" rules

Default postures. D1 is a default expectation and D8 a lower prior — the customer conversation can override both.

| # | Condition → result | Reconsider when | Meetings |
|---|---|---|---|
| D1 | Copilot seats materially unassigned/inactive → don't lead with expansion; lead with adoption (partner, masterclass, Alder) | Gap filled and impact shown; or stated expansion intent | M02, M03, M04, M13, M15, M16 |
| D2 | A5 features unused (fails ≥3-of-4 at ≥50%, Sentinel excluded) → no tier upsell; "activation, not sale" | Test passes; customer names a gap mapping to the tier | M04, M06, M09, M11 |
| D3 | A5 + Sentinel + heavy usage → no security upsell; at most CfS if in-house SOC | A "mega-specific" unmet need | M05, M07, M08, M12, M15 |
| D4 | Deliberate A3 + targeted add-ons → no A3→A5 pitch; add-ons/A7 only if asked | New gap or intent to consolidate | M06, M12 |
| D5 | Below masterclass minimums (>10 Copilot and >100 seats) → cannot nominate; partner/Alder for adoption | Seats grow past minimums | M01, M03, M06, M07, M09 |
| D6 | Masterclass/assessment as a commitment, or ownerless "would you be interested?" → don't; eligible accounts nominated proactively, "subject to nomination/availability", tied to adoption talk + child | Nomination confirmed; adoption conversation documented | M05, M13, excluded clip |
| D7 | Renewal within ~3 months (EES) → no in-renewal upsell expectation; top growth, calibrated effort | Addition already budgeted; or CSP/online | M03, M04, M06, M07, M09 |
| D8 | K-12 → Azure AI, Copilot Studio, GitHub Copilot, Copilot for students, innovation narratives = lower prior, not excluded | Customer raises topic or concrete initiative | M06, M12, M15 (M16 contrast) |
| D9 | Little on-prem or below >5 VMs → don't push migration/TCO | Modernisation/cost need; >5 VMs confirmed | M04, M09, M12 |
| D10 | Azure in-cloud expansion (architecture, scaling) → out of team scope | Scope changes; SS-led | M06, M08, M09 |
| D11 | Purchase invoiced before any engagement → don't pursue attribution or serious prep | New need beyond current licences | M11 (M13 counter-example) |
| D12 | No clear intention or trigger date → stop chasing | Concrete need with a date | M03 |
| D13 | Customer unresponsive + partner controls renewal + imminent → partner email only | Customer replies or partner reveals need | M16, M04 |
| D14 | Request for more free licences → "nothing there" | Customer asks for paid SKUs | M02 |
| D15 | Weak Power Platform / single Dynamics connector / Dynamics in education → don't lead | Stated ERP/finance/HR need | M07, M08, M09, M11 |
| D16 | Assessments and masterclasses depend on nomination/availability → never guaranteed | Slot granted | M05, M07 |
| D17 | Sentinel/CfS where security outsourced or attribution untrackable → mention only | In-house SOC; attribution confirmed (TS) | M02, M05, M06 |
| D18 | Pricing, discounts, quotes, POCs, implementation → never (role boundary) | Never | M02, M11, M13 |
| D19 | Child opportunity without proof of work → don't create | Recap, notes or aligned resource exists | M03, M11, M15 |

## 8. Discovery question library

Tags: **C** customer · **P** partner · **I** internal · **S** specialist. Eligibility per §9.1.

**Copilot adoption (existing seats)** — How has it gone; used for what? (C) · Why not all assigned; who has them? (C) · Impact so far; who gets the rest? (C) · Daily process or isolated use? (C) · Struggled to find value; skills gaps? (C, masterclass frame) · Who decides on more; what value must they see? (C) · Which group next? (C) · Purchased/assigned/active, tranches, expiring batches, agent/Cowork use; eligibility (I).

**First pilot (zero/tiny footprint)** — Is this a pilot; what makes it succeed; need guidance? (C) · What blocked the licences? (C, partner-support trigger) · Where could AI apply — admin, finance; try a few licences? (C) · How would you run and measure a pilot? (C) · Planning to buy N but test first? (C, partner-program cue) · Chat users; faculty vs student split (I).

**Security** — Base solid, or something missing? (C) · Known gap — users, identities, devices; incidents? (C) · How many run security; consoles; investigation time? (C) · Alert workload a pain? (C) · In-house or via partner? (C, Security Copilot gate) · Leavers/graduates; retention/deletion rules? (C) · What stops scaling AI access — labelling, governance, permissions? (C) · Minors'-data compliance; IT staff per devices? (C, K-12) · Security or staff workload — which hurts more? (C, K-12) · Active ÷ licensed per workload, free excluded; ≥3-of-4 at ≥50%; Sentinel/CfS presence; >100-seat eligibility (I) · Which assessment fits; how to request (S, SS).

**Data & Fabric** — What do you do with data; where; fragmented; time to visibility? (C) · Visibility across schools? (C, K-12) · Struggling with reporting or AI-ready data? (C) · How do you handle analytics today? (C) · Power BI counts; Fabric presence (I).

**Azure AI and agents (Higher Ed tendency)** — Where on your AI journey? (C) · Which processes have AI use cases — research, innovation, development? (C) · Building apps, chatbots or agents with LLMs? (C) · Need to share agents with students/unlicensed users? (C) · Explored a student curriculum/graduation assistant? (C) · Which Azure models; what are you building; stage; blockers? (C) · Researchers/developers need AI coding tools? (C) · Manual processes to automate — onboarding, intake, alumni lifecycle? (C) · Azure prepayments and what they consume (I) · Studio vs Foundry vs Fabric direction; pilot sizing (S, Alder).

**Migration** — Why still on-prem; can it migrate? / compared hybrid vs cloud cost? (C, technical/financial) · Why hybrid — dependencies, compliance; help with TCO? (C) · Which workloads remain; roughly how many VMs, not desktops? (C, >5 for assessment) · Migration plans; financial and technical case? (C) · Migrate for modernisation or cost? (C) · Still have on-prem workloads? (C, where CSP hides visibility) · Server lines → VM estimate; prepayment lines (I).

**Partner alignment** — Already working an opportunity; co-sell in progress? (P) · What do you know; what are you working on? (P) · Who is the account contact? (P) · What resources for identified needs; can you nominate them for your programs? (P) · Need help positioning or building business cases; security need for their AI journey? (P) · Introduce yourself; what are you quoting? (P, reseller) · Did you support pilot launch, training, measurement? (P).

**Renewal timing and channel** — Buy now, or must something happen first? (C) · Already budgeted an addition; buying anything else before renewal? (C) · Renewing; how much; changes? (C, CSP block then pivot) · Pay monthly or upfront? (C) · T-minus; agreement/channel; annual vs monthly; which tenant renews; currency (I).

**Opportunity validation** — What do you need from Microsoft to move forward before renewal? (C) · Anything blocking a process? (C) · Would a free assessment or expert session help? (C, subject to eligibility) · Opportunity created, contact started, purchase invoiced — when; same TPID/enrollment? (I) · Specialist forecast comment or Copilot tag present? (I, decides booking Alder).

## 9. Decision heuristics

### 9.1 Assessment & masterclass eligibility — confirmed by Alder (2026-09-29)

Single authoritative source; replaces every threshold spoken in sessions.

| Assessment / program | Minimum requirement |
|---|---|
| Azure Solution Assessment | > 5 VMs |
| Rapid Security | > 100 seats |
| AI-Ready Secure Foundation | > 100 seats |
| AI-Ready Productivity | > 300 seats |
| Copilot Master Class (Chat & M365) | > 10 Copilot licenses and > 100 seats |
| Copilot Master Class (Agents) | > 10 Copilot licenses and > 100 seats |

Nomination channels (internal): **MSX Deal Assistance** — Security & AI Business Solutions Assessments; **Azure Offer Navigator** — Cloud & AI Platform Assessments.

Posture: masterclass = **proactive nomination** whenever minimums are met; assessments offered once a need/blocker is confirmed; neither ever presented as guaranteed.

### 9.2 Heuristics

**FR** formal requirement · **RH** repeated (≥3 sessions) · **RH-t** repeated, confirmed as tendency/default · **IE** illustrative, not endorsed · **OC** one-time calculation, do not generalise · **TS** verify · **SUP** superseded.

| Heuristic | Class | Notes (meetings) |
|---|---|---|
| Segment (K-12 vs university) shifts conversation probabilities | RH | Parallel first step with T-minus (M01, M07, M09, M15, M16) |
| T-minus decides in-renewal vs top growth | RH | Parallel first step with segment (M03, M04, M07) |
| Top growth lands months after renewal; school renewal purchases decided ~6 months earlier; "T-minus 6" = in-agreement sale plausible | IE | Single sources, not endorsed (M08, M09) |
| CSP/online auto-renews; renewal is a legal pretext; discovery-led growth | RH | Buying-timing only (M05, M11) |
| Pilot boundary ≈ 25 seats — estimate the conversation can move | RH-t | M01, M03, M10, M13 (re-labelled), M07 (tiny pilot expansion-ready) |
| ≈90%+ adoption → expansion; mostly unassigned → unlikely to buy | RH-t + IE | Default (M05, M08, M10, M12) |
| Unassigned paid seats → ask why → masterclass hook | RH | Nomination proactive when eligible (M02, M12, M13) |
| >10 seats with very low adoption → masterclass | RH | Consistent with §9.1 (M16) |
| Nobody buys more of what didn't work | RH-t | Default, not hard rule (M09, M12, M15) |
| Large Copilot sales pass through a pilot; adoption problems → partner mostly, else Alder; few paid seats + many Chat users → expansion signal | IE | M02, M03, M11 |
| Masterclass: >10 Copilot and >100 seats | FR | §9.1; spoken variants M01, M03, M05, M06, M08, M12 |
| Masterclass acceptance ≠ business opportunity | RH (single) | Still needs a child (M13) |
| Rapid Security / Secure Foundation >100; Productivity >300; Azure Solution Assessment >5 VMs | FR | §9.1; "Rapid Security no longer exists" (M07) superseded |
| Masterclass session formats; education-specific assessment with own minimum/slots | SUP | Not in confirmed table (M03, M05, M06, M07, M15) |
| Eligibility counted on active licences, not future purchases | FR + TS | M05 |
| AI-Ready assessment unnecessary with A5 at scale; Purview portal readiness assessment for A5 | RH + TS | M12, M15 |
| Security ladder Defender → XDR → Sentinel → CfS | RH | M02, M03 |
| Usage test: ≥3 of 4 workloads at ≥50% active ÷ licensed; Sentinel not counted | FR | Canonical (M09, M11; Alder) |
| "4–5 checks" version of the usage test | SUP | Transcript artefact (M06) |
| Compute active ÷ licensed; exclude free seats | RH (method) | M06 |
| A3/A5 imbalance alone is not an A5 signal | RH (single) | M09; consistent with M12 |
| A3 + add-on mix = licensing already optimised | RH | M06, M12 |
| Never quote price; partner quotes and discounts | RH (role) | M02, M11, M13 |
| A3 = base to start AI; A5 needed to scale (auto-labelling, auto-response) | RH | Core (M10, M13, M15, M16) |
| A3 + high Copilot adoption → both tracks; security first when unsure | FR | Resolved (M10, M13, M16) |
| Security not a hard prerequisite for a curated-data pilot | RH (single) | M01 |
| Copilot target = faculty/admin; A5 count ≈ faculty headcount | RH-t | M12 |
| K-12: security (minors' data) + IT workload most likely themes | RH-t | M06, M07, M09, M15 |
| K-12 mainly Google/Chrome OS → Copilot for admins; innovation plays lower prior | RH-t | Not exclusion (M12, M15, M16) |
| Universities: research, IP, innovation → broad AI/Azure/Fabric/GitHub; "find where to apply AI" | RH-t | M01, M03, M07, M10, M13, M16 |
| Power BI without Fabric → Fabric via fragmented data | RH | M05, M09, M10, M12 |
| Server lines → rough VM estimate → assessment candidate or below minimum | OC + TS | Illustrative; per-core coverage unverified (M01, M08, M09) |
| "Most Copilot accounts already have A5"; "large Azure spend → remaining on-prem necessary"; "K-12 hybrid by compliance" | IE | Single sources, not endorsed (M13, M12, M15) |
| Team sells Azure only as migration | FR (scope) | M06, M08, M09, M15 |
| Partner incentives may exist; handled by partner; never promised | RH (role) | M13, M15 |
| Attribution = child + relevant documentation | FR | Resolved (M10, M11, M15, M16) |
| Partner before customer | RH | M02, M03, M09, M13, M15 |
| Every meeting ends with outcome + booked next step | RH | M06, M08 |
| Book Alder: accepted meeting, ≥1 day ahead, short slot, top deals first, Copilot-flagged/commented only | FR (process) | Evolving (M08, M12, M15) |
| Specialist involvement high level | FR (role) | Resolved (M15; Alder) |
| A7 GA 1 Oct 2026; later renewals eligible; includes Copilot + security | FR (assumed GA) | §10 (M09, M12, M13) |
| A0 replaces student benefit; A2 for Chromebooks; Copilot on A1 | FR (assumed GA) | §10; spoken ratios/dates not relied on (M02, M08) |
| University attack-probability statistic; share of customers not paying for student licences; partner renewal uplift | IE + TS | Unsourced (M10, M08, M07) |

## 10. Conflicts, unknowns, assumptions

**Resolved contradictions (Alder, 2026-09-29)**
- Security first vs AI first (M01, M13, M16 vs M10, M12) → A3 + high adoption: both tracks; security first when unsure.
- Masterclass posture (proactive M08; hook M12; conditional M10, M13; "doesn't apply" M09) → proactive when §9.1 met; never a commitment; tied to child + adoption talk.
- Attribution proof ("one resource suffices" M10 vs multi-element M11, M16) → child + relevant documentation.
- Specialist depth ("no more in-depth consultations" M15 vs live scoping M08, M13) → high level; live participation fine.
- Framing order (segment first M01, M09, M15, M16 vs T-minus first M07) → parallel.
- Usage test ("4–5 checks" M06 vs ≥3-of-4 M09, M11) → ≥3 of 4 at ≥50%, Sentinel excluded.
- Pilot boundary → ~25 seats, an estimate.
- Sentinel varies by account (callout M01, lead M03, probe M04, maybe CfS instead M10) — legitimate; constant = workload reduction where Defender/XDR used.

**Superseded (record only):** spoken masterclass minimums and session formats; "Rapid Security no longer exists" (M07); education-specific assessment (M05, M07); "T-minus 6", "most Copilot accounts have A5", "large Azure spend → on-prem necessary", "K-12 hybrid by compliance" — single-session illustrations.

**Assumed GA (Alder):** A7 (GA 1 Oct 2026, Copilot + security components; later renewals eligible), the A0/A2 student-licensing change, Copilot on A1. Treat as current; spoken ratios, dates, price impacts not relied on.

**Still [TIME-SENSITIVE — verify]:** Identity Lifecycle not in Entra P2 — via A5 / Entra ID Governance / Entra Suite, per-user requirement; Purview DLM plan mapping; A5 includes Power BI Pro; agent-sharing limits with unlicensed users; GitHub Copilot education tier; Purview portal readiness assessment for A5; eligibility on active licences; CSP auto-renewal and monthly-commit invoicing; consumption attribution for Sentinel/CfS/Cowork; server per-core coverage; renewal-uplift, student-licence-payment and attack-probability statistics.

**Out of scope (removed):** all pricing and billing models; incentive programs and amounts; test-licence programs; Azure funding details; expected-close-date rules; fiscal-year measurement and closure metrics; government/GCC tiers; nonprofit licensing.

**Thresholds:** all resolved (pilot ~25 estimate; §9.1 minimums; ≥3-of-4 at ≥50%; >5 VMs).

**Unresolved account-level questions:** Identity Lifecycle per-user licensing (Alder); Sentinel near-zero — trial or abandoned (M01, M02, M13); Dynamics grace-period anomaly (M02); consumption attribution (M02, M03); currency vs book (M04); CSP payment cadence (M05); paid base tier? (M06); second agreement (M09); location vs stated name, two TPIDs (M13); pilot figures actual? (M15); earmarked-budget origin (M16).

**Illustrative-only patterns [I] — never thresholds:** large idle share demotes expansion despite good use of assigned seats; ≈90% active = healthy (tendency); many student identities vs small team → consumption-layer security; many Power BI seats → Fabric; faculty-tier count as headcount proxy; prepayment lines → migration-room context; server lines → VM estimate; small AI prepayments → live project.

**Evidence gaps:** single 2.5-week window; 7 untranscribed; seller audio unusable in ≥5; several garbled figures; no customer outcomes — nothing validated; canonical usage test rests on two sessions + Alder's confirmation; multi-tenant/two-TPID cases show input data-quality risk.

## 11. Communication style

**Uncertainty** is explicit — "probably", "could easily be", "this is a hypothesis"; callout ≠ recommendation; live self-correction; blunt candour ("honestly, not much potential"). **Hypotheses** are "the most probable scenarios"; the forecast comment is "a best guess" to cover, not obey; the customer is the only validator. **Coaching** pushes need over product ("don't be product-oriented"), pattern recognition then booking the specialist, and closes ownerless offers; analogies (CSP as a streaming subscription, resellers as supermarkets) and Socratic prompts ("what would you offer?"). **Translation:** identity lifecycle → "who left, which licence for a graduate"; Sentinel → "the workload drops dramatically"; A5 → "you no longer label manually"; Cowork → "delegate whole tasks"; assessments → "a Microsoft person with resources, for free". **Prioritisation** is always an ordered list; rejections data-backed and blunt ("not a chance", "that revenue already died"). **Ownership** by function: seller owns meeting, child, follow-up; Alder owns high-level discovery and notes; partner owns quotes, MVPs, incentives.

Language layers:
- *Internal analysis:* white space, callout, trigger, T-minus, top growth, active ÷ licensed, "pilot to production / scale and transform", "the room is closed".
- *Seller coaching:* "take the framework, not the answer"; "don't give it so much fire"; "never get blocked"; "get on the bus early".
- *Customer-facing:* "is this a pilot?"; "what do you need from us to move forward?"; "before we scale, let's get security right"; "see me as a resource to access Microsoft programs".
- *CRM / forecast:* "forecast comment", "child opportunity", "build vs consumption child", "proof of engagement", "measure committed, not invoiced", "no specialist comment = no strategy yet".

## 12. Decisions applied + open items

**Decisions applied (Alder, 2026-09-29)**
1. T-minus and segment are parallel first steps.
2. Adoption before expansion = default expectation, not hard rule.
3. Pilot boundary ≈ 25 seats, an estimate.
4. Security usage test = ≥3 of 4 workloads at ≥50%, Sentinel excluded; "4–5 checks" superseded.
5. One-time calculations marked illustrative; converted to pattern descriptions.
6. "T-minus 6" / "most Copilot accounts have A5" / "large Azure spend → on-prem necessary" / "K-12 hybrid by compliance" = illustrative, not endorsed.
7. A3 + high Copilot adoption → both tracks prioritised; open with security when unsure.
8. Masterclass = proactive nomination when eligible.
9. Attribution proof = child opportunity + relevant documentation.
10. Specialist involvement is high level.
11. Downgrade routing removed.
12. Government/GCC content removed.
13. Pricing removed; role boundary kept.
14. Incentives, test-licence program, Azure program details, expected-close-date rules, measurement model and closure metric removed; neutral "partner incentives may exist" kept.
15. Nonprofit out of scope; retained as evidence only (M14).
16. Missed-attribution amount and story removed; M11 kept as attribution post-mortem.
17. Authoritative eligibility table added (§9.1); older thresholds superseded.
18. A7, A0/A2 change, Copilot on A1 assumed GA (1 Oct 2026).
19. Verification list trimmed to in-scope items.
20. Institutions, acronyms and partners anonymised.
21. Account numbers kept as session facts only, not thresholds (removed entirely here).
22. K-12 exclusion list → lower prior.
23. Higher Ed inclusion list and "find where to apply AI" → tendencies.
24. Channel = buying-timing dimension only.
25. Section 12 replaced with decisions list + open items.
H. Executive summary re-aligned; matrix recounted (104 rows); reader-facing wording; evidence discipline preserved.

**Remaining open items for Alder**
- [ ] **Identity Lifecycle and Purview plan mappings** — licensing vehicle for Entra Identity Lifecycle (A5 / Governance / Suite; per-user) and the Purview plan carrying DLM.
- [ ] **Agent-sharing limits** — confirm declarative agents cannot be shared with unlicensed users (Studio trigger, M08).
- [ ] **Remaining licensing claims** — A5 includes Power BI Pro; GitHub Copilot education tier; Purview portal readiness assessment for A5 customers; eligibility counted on active licences.
- [ ] **Consumption attribution** — whether Sentinel / CfS / Cowork consumption tracks to the seller, and how (affects P10, D17, Sentinel rows).
- [ ] **Numeric bands for adoption** — "≈90%+ active" (expansion) and "materially unassigned" (demotion) stay tendencies unless you state explicit bands.
- [ ] **Evidence limits** — single 2.5-week window, no customer outcomes; re-review when discovery and later prep transcripts exist.
