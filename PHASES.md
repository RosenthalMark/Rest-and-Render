# Rest and Render — Development Roadmap

Status: planning draft for owner review. No implementation phase has been approved or completed.

This document defines the development process and proposed phases. Approval of the roadmap is not permission to execute every phase. Each phase needs its own GO, review, and two signoffs.

## Product direction

An art-driven sticker and greeting card shop for the owner's sister in Texas, with development managed remotely near St. Louis. One business sells its own products; this is not a multi-seller marketplace.

Shopping and listing management should be familiar in the way Etsy is familiar, while the visual identity is custom. Priorities include mobile-first shopping and administration, themed collections, sets, limited products, configurable deals, custom sticker requests, and distinctive sticker vending machines. The immersive 1990s experience is a major product ambition, not incidental decoration.

The user owns creative decisions. Artwork, palette, hero imagery, and explicit feedback will guide design. Stripe's standard sale-based payment-processing fees are an approved exception to the free-only rule. Before implementation, verify current fees and disclose any other possible charges. Paid Stripe add-ons or services require separate approval. No other paid service or final stack has been approved.

## Working agreement — applies to every phase

### Start gate

Before implementation, present the phase plan in chat with:

- Objective and what should be working at the end.
- Included work, exclusions, dependencies, and affected systems.
- Design decisions, proposed services, costs, and open questions.
- Technical verification and human-verifiable acceptance checklist.
- Proposed branch and whether remote pushing is authorized.

Ask for an explicit **GO / NO-GO** and wait for GO. Finishing one phase does not authorize the next. Read-only investigation may inform the brief, but must not turn into unapproved implementation.

### Decision ownership and better ideas

- The user approves design, visual identity, and customer-facing creative choices unless they explicitly delegate that freedom.
- The assistant handles routine technical choices within approved scope and explains material tradeoffs.
- If a better approach exists, explain the requested approach, the alternative, why it may be better, and the costs or compromises. Do not silently replace the user's intent.
- Major open-source starters, frameworks, and service integrations require approval before adoption. Review licenses, maintenance, limitations, and operating costs.
- Material scope or design changes require an updated brief and renewed GO.
- Keep folders purposeful. Reuse existing asset locations; do not create parallel asset trees without a concrete reason.

### Project-wide cost boundary

- Use free options only. Do not select, subscribe to, purchase, activate, or depend on any paid service, tool, signing certificate, hosting tier, or future paid upgrade to keep the project working.
- A recommendation is not approval. Before any exception can be considered, present the full one-time, recurring, usage-based, and conditional costs, who would pay, and the free alternatives; payment requires the user's explicit approval after review.
- Before recommending a service, verify and explain its current free-plan limits and what happens when each relevant limit is reached. Do not assume an upgrade is the solution; pause and present free alternatives or a simplified feature.
- Stripe's standard sale-based processing fees are the one approved exception. Verify current fees and disclose other possible charges before implementation; do not select paid Stripe add-ons or services without explicit approval. Other transaction fees require separate approval.

### Git, push, merge, and deployment rules

- Keep `main` reviewed and usable. Use focused phase branches; split large changes into reviewable pull requests when appropriate.
- Review the staged file list and diff before committing. Never include credentials, unrelated files, or unapproved large artwork originals.
- Verify ignore rules before the first staging operation. Ignoring a file does not remove it from prior Git history.
- Establish push authorization at kickoff. If not authorized, prepare changes locally and ask before pushing. No automatic push to `main`.
- A branch push is a review checkpoint, not permission to merge or deploy.
- Merge only after relevant checks pass, blocking findings are resolved, and both user and assistant signoffs are recorded for the reviewed commit.
- Material changes after signoff require renewed review. Administrative updates that only record the signoff must not conceal code changes.
- Deployment requires explicit authorization for the identified release; merging does not imply deployment permission.
- Do not force-push or rewrite shared history without explicit approval.

### Completion gate and signoff record

At phase end, report what changed, how to inspect it, checks and results, known limitations, and the human checklist. Never mark a check complete based only on intended behavior.

Use this record for every phase:

```text
Phase:
Kickoff GO: pending | user approval reference and date
Approved scope / exceptions:
Push authorization: not granted | approval reference
Review target: commit SHA, or document revision for planning-only work
Technical checks and evidence:
Human checks and evidence:
Unresolved issues:
Assistant signoff: NOT READY | PASS, with date and reasons
User signoff: PENDING | CHANGES REQUESTED | APPROVED, with date
Merge authorization / result:
Deployment authorization / result, if applicable:
```

The assistant may not manufacture user approval. The user need not accept the assistant's recommendation. A phase is complete only when both signoffs are present and its acceptance criteria are met. Approval to merge may be recorded with user signoff if explicitly stated.

## Folder and document responsibilities

| Location | Purpose |
| --- | --- |
| `1997 Vending dreams/` | References, artwork, skins, and other assets for the 1990s machine experience. |
| `Assets/` | General website art: hero imagery, branding, backgrounds, and decorative graphics. |
| `ART/` | Local product originals, print-ready files, and design sources. |
| `LOCAL-SECRETS/` | Local credentials, excluded from Git. Contents are not documentation or deployment assets. |
| `PHASES.md` | Roadmap, working agreement, phase gates, and review records. |
| `WISHLIST.md` | Append-only idea history; shipped items remain crossed out with a release reference. |
| `README.md` | Project overview and local folder guide. |
| `AGENTS.md` | Concise instructions for agents working in this repository. |
| `TECH-STACK.md` | Approved and undecided technology, account references, and cost rules; no secrets. |
| `CHANGELOG.md` | Production releases actually shipped. |

Create further documents only as needed, such as operating instructions when actual procedures exist. Account documentation records service URLs, owners, and credential locations, never secret values.

Product records belong in the database; customer-facing uploaded images belong in media storage. Local ART holds originals. The deployed shop must not depend on a folder on either person's computer. Decide what art belongs in Git after inspecting types and sizes, without automatically committing all existing art.

## Phase 0 — Repository and documentation foundation

**Purpose:** establish a clean project with clear rules before application code.

**Work:** preserve existing folders; create ignore rules before staging; connect the local folder to the existing GitHub repository without overwriting assets; inspect the proposed tracked files; establish the minimal README and project instructions. Keep the stack/access record small and create operational documents only when there are real procedures to describe. Add a changelog with no invented releases.

**Expected result:** understandable documentation and a clean repository ready for approved work. Repository visibility is currently public; review tracked content accordingly. Creating the roadmap does not itself complete this phase.

**Human acceptance**
- [ ] Existing artwork and folder names are preserved.
- [ ] Folder purposes and the development agreement are understandable.
- [ ] `LOCAL-SECRETS/` and environment secrets are demonstrably excluded from Git.
- [ ] The proposed tracked files contain no secrets or unapproved large originals.
- [ ] All requested ideas are represented in the wishlist.
- [ ] User approves the repository organization and intended public content.

**Done when:** repository hygiene is verified and both parties approve the foundation.

### Phase 0 review record

- Kickoff GO: user approved the stated local-only scope on 2026-10-30.
- Approved scope: local Git initialization, minimal documentation, asset metadata inspection, and ignore verification; no installations, paid-service decisions, staging, commits, or pushes.
- Review target: local working-tree documents; no commit exists.
- Push authorization: not granted. Merge and deployment are not part of this phase.
- Technical checks and evidence: local Git branch is `phase-0` and `origin` matches the supplied URL; the index is empty; ignore checks cover secrets, environment files, OS metadata, and the three artwork directories. Asset metadata inspection found only four `.DS_Store` files; their names and sizes were unchanged on recheck. Documentation check found phases 0–12, 28 unique wishlist entries, a consistent Stripe exception, and no claimed production release.
- Human checks: user reviewed the Phase 0 result and passed it on 2026-10-30.
- Assistant signoff: PASS, 2026-10-30, for the approved local-only scope and checks above. User review and signoff remain outstanding.
- User signoff: APPROVED ("pass"), 2026-10-30.
- Phase status: complete for the approved local-only scope; both signoffs recorded. The next phase requires its own brief and GO.

## Phase 1 — Selling rules and first-launch scope

**Purpose:** define what the business sells and what launch must include.

**Work:** define sticker and greeting-card variants, materials, finishes, envelopes, personalization, ready-to-ship versus made-to-order items, and shipping/fulfillment responsibilities. Distinguish collections (browsing groups), sets (purchasable bundles), and limited editions (constrained supply). Decide whether sets consume component stock. Define guest/account expectations, custom-request handling, and the operating budget. Decide launch machine scope and chosen-product versus mystery behavior, including assignment/reveal timing.

**Expected result:** an approved launch specification and explicit later work.

**Human acceptance**
- [ ] Walk through selling a sticker, greeting card, set, and limited item.
- [ ] Walk through receiving, packing, shipping, and updating an order.
- [ ] Identify launch requirements versus later wishlist items.
- [ ] Confirm machine sales behavior and shipping regions.
- [ ] Confirm the acceptable recurring-cost boundary.

**Done when:** no unresolved sales rule blocks architecture or launch planning, and both parties sign off.

### Phase 1 working record

- Kickoff GO: user approved the stated planning-only scope.
- Approved scope: discuss and document products, inventory, fulfillment, requests, machines, and launch priorities; append new wishlist ideas as needed.
- Push authorization: not granted. No staging, installation, paid-service decision, merge, or deployment.
- Review target: local planning documents; no commit exists.
- Technical and human checks: pending the agreed product scenarios and user review.
- Assistant signoff: pending.
- User signoff: pending.
- Phase status: in progress.

#### Product discovery so far

- The owner's sister mostly makes or prints the products herself, using her watercolor artwork and a high-quality printer.
- Themed sticker packs observed so far include Halloween and succulents, each roughly 10–14 relatively large stickers. These are examples, not a fixed pack-size requirement.
- Premium presentation is part of the experience: polished packaging, labels, and a collection card with corresponding artwork. Product pages should eventually communicate the full package, not only individual sticker designs.
- The observed greeting card had professional-quality finishing, with branding and text on the back. Card formats, envelopes, and options are undecided.
- Each collection can decide whether its individual stickers are also sold separately; full packs remain supported.
- Each collection can use independently tracked pack and single stock or have packs consume individual sticker stock. How those choices interact with made-to-order products needs design and verification.
- Listings can be ready to ship or made to order, depending on the product. Show a shop-wide production-time estimate for made-to-order items, and allow the sister to pause an individual listing or all made-to-order orders. Custom orders take 2–4 weeks depending on design; orders over 100 stickers are also subject to 2–4 weeks of processing. Whether that range applies to all other made-to-order listings, the start of the clock, and stock rules remain open.
- The sister intends to ship to the US and Canada, directly from the post office on Saturdays, replacing the earlier worldwide goal. Pickup is offered in Hays or Comal County, Texas; orders are paid online, then arranged privately by email for ordinary requests or business Facebook Messenger for quicker answers. Do not display a phone number. Flat shipping rates, exact pickup arrangements, customs, and contact destinations remain open; contact links do not imply automated messaging or a paid integration.
- Launch ambition: the shop and a surprise 1990s section with roughly 3–4 machines, at least one working if feasible, plus differently shaped future machines decorated with coming-soon bags or stickers. Decide how many beyond the first work after prototyping. Prototype both a first-person space and an interactive cabinet gallery, then choose the launch direction. Reuse machine behavior and support reskinning; visibly unavailable machines must not suggest they can be purchased from yet.
- Products sold through the machines are physical stickers only. Digital products, digital stickers, and digital collectibles are out of scope. Whether the first working machine offers customer-selected stickers, mystery stickers, or both remains undecided; revisit after prototyping and discussing fulfillment.
- A custom sticker request is paid on submission at a fixed price per sticker; the customer chooses a quantity. The sister will fulfill custom orders, with up to three different designs; processing takes 2–4 weeks depending on design, starting when the order is placed. A 100-sticker minimum was initially mentioned, but is now uncertain and must not be treated as a requirement. A possible $4 per sticker was suggested tentatively and needs confirmation; allocation among designs remains open. The separate rule that orders over 100 stickers are subject to 2–4 weeks of processing was stated by the sister and should be confirmed along with the minimum. If the sister cannot make the request, she contacts the customer and offers a refund. Included work and other review/refund policies need agreement before launch. Prototype a customer drawing pad before deciding whether it is required at launch. Optional AI-assisted design remains an idea; AI costs, privacy, limits, ownership, feasibility, and approval remain unresolved. Greeting-card personalization is still a proposal to discuss with the sister.
- Sold-out limited releases stay visible with a sold-out status. Deal management supports percentage discounts, fixed-dollar discounts, and manually set sale prices; only one deal may be active at a time. Scheduling details remain open. Guest checkout is required; customer accounts may come later.
- Shipping charges use flat rates by destination or region. Specific US and Canada rates remain to be worked out; do not offer other destinations without a new decision.
- The user and his sister each have a separate administrator login, and orders, statuses, and tracking are managed in the CMS. Send order confirmation and shipping/tracking updates to customers. Newsletter signup and an automatically updated Instagram and Facebook feed are launch goals; assess each platform's free access and limits before recommending an integration. If the feed is unavailable or no suitable free integration exists, fall back to curated posts and account links.
- Customers may request returns or cancellations for ordinary products within a defined period; the duration and conditions remain to be agreed with the sister. Clearly disclose possible international import charges before purchase; confirm wording and responsibilities.
- Sister's question list: shipment day and countries, pickup counties, custom-order willingness, maximum designs, and custom processing window answered. The previously stated custom minimum is uncertain. Product launch selection, other production timing, actual custom price and design allocation, shipping rates, exact pickup arrangements, returns/cancellations, and business contact and social account details remain open. Keep the 1990s machine surprise private.

## Phase 2 — Art direction and interaction design

**Purpose:** make the experience distinctive using the supplied artwork.

**Work:** review palette, hero image, references, and machine assets; present a small number of meaningfully different directions; choose playful but readable typography; define product presentation, custom navigation, responsive layouts, and motion. Preview mobile homepage, product page, listing workflow, and a machine concept. Agree how the modern gallery and nostalgic environment relate to the main store.

**Expected result:** approved representative screens and an actionable visual brief, not merely a mood board.

**Human acceptance**
- [ ] The identity feels custom and matches the user's intent.
- [ ] Text is readable and product artwork takes priority.
- [ ] Hero and navigation explain where to shop and explore.
- [ ] Mobile layouts and controls feel comfortable.
- [ ] User explicitly approves the direction and motion examples.

**Done when:** the user approves creative direction and the assistant confirms implementation feasibility and accessibility considerations.

### Phase 2 working record — homepage directions only

- Kickoff GO: user approved the local implementation scope in chat on 2026-11-01.
- Approved scope: create two responsive, local homepage concepts at separate paths for comparison: a neon video direction with a one-time muted intro and the supplied poster fallback, and a blue watercolor direction. No other shop pages, stack choice, or production work.
- Push authorization: not granted. No staging, commit, push, merge, or deployment is included.
- Review target: local mockups in `mockups/homepage-directions/`; no commit exists.
- Technical and visual checks: standalone HTML/CSS/JS; no packages or external services. Local media references are present. The supplied video is 9.07 seconds at 1920×1080. Following owner feedback, the neon concept displays the muted video alone in the viewport, then reveals the supplied page artwork and poster. A session guard skips the intro on a same-tab return; reduced motion and playback failure use the finished state. The implementer visually checked playback, completion, return, and reduced motion at desktop sizes. The flattened artwork may leave black space or require scrolling on some screens when shown in full.
- Human checks: pending owner comparison and direction approval. The broader Phase 2 previews (product page, listing workflow, and machine concept) remain outside this GO.
- Assistant signoff: PASS, 2026-11-01, for the two approved homepage concepts and visual/accessibility review; video runtime persistence is not claimed as browser-verified.
- User signoff: PENDING.
- Phase status: in progress; awaiting human review and creative-direction approval.

## Phase 3 — Reusable foundations and stack approval

**Purpose:** reuse good software rather than rebuild solved problems, within the project-wide free-only boundary.

**Work:** compare commerce/CMS candidates using realistic owner tasks; evaluate database, hosting, media storage, email, Stripe integration, animation, and 3D tools. Check commercial-use licenses, maintenance, costs, free-tier limitations, exportability, and upgrade burden. Research reusable vending-machine work without assuming a complete suitable implementation exists. Demonstrate creating a listing from a phone and investigate last-item inventory handling. Obtain approval before adopting major candidates.

**Research leads, not selected dependencies:** Payload ecommerce, Medusa, Supabase Postgres, Motion, and Three.js/React Three Fiber. Recheck current documentation before selection.

**Expected result:** an approved stack with evidence for its suitability and a clear division between reused and custom work.

**Human acceptance**
- [ ] Owner can follow the proposed listing workflow.
- [ ] Costs, limits, and operational responsibilities are visible.
- [ ] Each major foundation has explicit approval.
- [ ] Custom work and inherited limitations are understood.

**Done when:** user approves stack and costs; assistant verifies the technical approach.

## Phase 4 — Application foundation and environments

**Purpose:** establish a running application and safe review workflow.

**Work:** scaffold only the approved stack's required directories; configure development and preview environments, database, media storage, admin access, environment variables, and relevant automated checks. Separate test payments from live payments. Document startup and initial recovery procedures. Add stack-specific ignore rules before generated files appear.

**Expected result:** a running preview with protected administrative access.

**Human acceptance**
- [ ] Open the preview on a phone and desktop.
- [ ] Sign in and out as an administrator.
- [ ] Verify visitors cannot access administrative functions or protected data.
- [ ] Follow the documented local startup procedure.

**Done when:** both parties verify the foundation works and is ready for feature development.

## Phase 5 — Mobile catalog, inventory, and CMS

**Purpose:** make everyday store management practical from a phone.

**Work:** implement listing drafts, photos and ordering, descriptions, variants, prices, stock, duplication, preview, publishing, archiving, and restocking. Support stickers, cards, sets, collections, and approved limited-release behavior. Add homepage content controls, featured items, gallery content, and configurable promotions. Define promotion scheduling, expiration, overlap, and sold-out behavior. Provide clear save/upload/error feedback.

**Expected result:** the owner can create and maintain real listings and homepage content without code edits.

**Human acceptance**
- [ ] Create and publish a sticker on a phone.
- [ ] Upload and reorder photos, set variants, and adjust stock.
- [ ] Create a greeting card and set with correct inventory behavior.
- [ ] Preview and publish content changes.
- [ ] Schedule a deal and verify its start, end, and sold-out behavior.
- [ ] Archive and restock a product without losing needed records.

**Done when:** user approves usability and assistant verifies data integrity and access controls.

## Phase 6 — Local ART workspace setup for Windows and Mac

**Purpose:** help the owner create an understandable local artwork workspace from a CMS entry point.

**Work:** present a clearly explained action such as “Set up my local ART folders.” Explain that these are local originals, separate from uploaded website images. Compare free browser-assisted setup, a free downloadable script/helper, and animated manual instructions. The earlier signed-helper recommendation is not approved and must not be selected or built. Present costs and limitations and obtain explicit approval of an approach before implementation. Each managed folder receives a short instructional `.txt` file explaining its purpose. Keep the structure small and approve it before implementation.

A hosted website cannot silently run an arbitrary local script. A browser-assisted flow requires supported browsers and explicit folder access. Test whether it can satisfy the non-overwrite guarantee under concurrent changes; do not claim exclusive file creation without evidence. Offer a manual walkthrough if automatic setup cannot safely meet the requirements. A downloadable helper or script must let the user choose the destination when run, and explain platform warnings without disabling security protections.

Setup must preserve existing files, handle paths with spaces, safely repeat, allow cancellation, and clearly report created/existing/skipped/failed items. Do not overwrite user-edited instructions. Local setup does not imply persistent folder access, backup, synchronization, or automatic upload.

**Expected result:** a tested setup flow on both operating systems, with understandable instructions and no destructive behavior.

**Human acceptance**
- [ ] On Windows, choose a test parent folder and complete the approved setup flow.
- [ ] Repeat on macOS, including the manual fallback where applicable.
- [ ] Read each folder's instructions and understand how it is used.
- [ ] Repeat setup without overwriting art or customized instructions.
- [ ] Cancel without unwanted changes.
- [ ] Try a destination without permission and receive a useful explanation.
- [ ] Verify no files upload merely because local setup ran.

**Done when:** user approves the workflow and instructions; assistant verifies both platforms and preservation behavior. If a platform cannot be tested, disclose that and leave its check open.

## Phase 7 — Storefront and dependable commerce

**Purpose:** make ordinary shopping work before connecting machine sales.

**Work:** build approved hero, hamburger/navigation, featured sections, catalog, product pages, collections, greeting-card section, gallery entry points, cart, and deal displays. Integrate Stripe with authoritative server-side price/stock validation and payment-event handling. Define reservation expiration/release, order confirmation, fulfillment, and agreed cancellation/refund behavior. Do not treat a browser success screen as proof of payment.

**Expected result:** customers can buy and the owner can fulfill orders reliably.

**Human acceptance**
- [ ] Complete a mobile test purchase and verify order, payment, and stock.
- [ ] Fulfill a test order and check customer communication.
- [ ] Attempt to buy sold-out stock.
- [ ] Have two checkouts compete for the last item; do not oversell.
- [ ] Verify failed/abandoned checkout releases reservations as designed.
- [ ] Close the browser after payment and verify the order still records correctly.
- [ ] Repeat a payment notification without duplicating orders or reducing stock twice.

**Done when:** user approves shopping and fulfillment; assistant verifies payment and inventory correctness.

## Phase 8 — Reusable, reskinnable sticker machine

**Purpose:** deliver the signature machine interaction on top of reliable commerce.

**Work:** implement the approved purchase mode, separating machine behavior, skin assets, product assignments, and selling rules. Build browsing, selection, coin/handle interactions, cardboard dispensing, and reveal using approved art. Connect to existing order and stock logic. Add loading, sold-out, interrupted, reduced-motion, and accessible alternatives; sound is optional. Prototype a second skin to prove reuse.

For mystery mode, implement only the explicitly approved promise, allocation, reveal, duplicate, and failed-payment rules. One-of-one products must use authoritative inventory protection; animation cannot decide availability.

**Expected result:** one polished working machine and demonstrated reskinning without duplicate sales logic.

**Human acceptance**
- [ ] Use and purchase through the machine on phone and desktop.
- [ ] Receive the product/selection promised by its approved rules.
- [ ] Verify sold-out and interrupted behavior.
- [ ] Reload without rerolling or duplicating a completed purchase.
- [ ] Apply a second skin without rebuilding the commerce flow.
- [ ] Use the alternative controls without sound or elaborate motion.

**Done when:** user approves the feel and appearance; assistant verifies sales and interaction reliability.

## Phase 9 — Immersive 1990s space and modern gallery

**Purpose:** deliver first-person machine browsing and expressive art presentation.

**Work:** prototype one short navigation sequence and one machine before expanding. Validate touch controls, camera movement, device performance, and loading. Build the approved environment from supplied assets, connect machines, and keep cart, exit, and conventional shopping easy to reach. Give the modern art gallery its own approved presentation where appropriate. Provide a usable alternative when 3D is unavailable; avoid loading the whole environment on the homepage.

**Expected result:** an enjoyable immersive space that remains usable on ordinary devices.

**Human acceptance**
- [ ] Enter, navigate, use a machine, and exit without coaching.
- [ ] Test on an ordinary phone, not only a development computer.
- [ ] Reach cart and normal shopping from the environment.
- [ ] Verify reduced-motion and unavailable-3D behavior.
- [ ] User approves atmosphere, artwork presentation, and transitions.

**Done when:** user approves the experience and assistant verifies agreed performance/accessibility targets.

## Phase 10 — Custom requests, newsletter, and social

**Purpose:** support customer relationships beyond checkout.

**Work:** implement the approved custom sticker request flow, including practical details such as quantity, size, finish, deadline, notes, and references. Decide at kickoff whether quotes/approval are handled in-app or through email. Add newsletter subscription/unsubscription and approved social links or curated content. Establish where the owner manages requests, delivery failure behavior, and relevant validation/abuse controls.

**Expected result:** customer submissions reach a real, manageable destination.

**Human acceptance**
- [ ] Submit and receive a custom request with its reference artwork.
- [ ] Follow the agreed review and response workflow.
- [ ] Subscribe and unsubscribe successfully.
- [ ] Update social content using the intended interface.
- [ ] Verify failed submission feedback does not claim success.

**Done when:** user approves administration and assistant verifies delivery and customer feedback.

## Phase 11 — Launch readiness and production release

**Purpose:** verify the approved launch scope and release it deliberately.

**Work:** review mobile/desktop behavior, keyboard and reduced-motion access, performance, real content, links, search metadata, and share previews. Verify owner access, domain/live configuration, backups, restore, rollback, error reporting, order communication, and fulfillment readiness. Prepare a concrete release summary and obtain explicit deployment authorization. Deploy, perform production smoke checks, then record what actually shipped.

**Expected result:** a functioning production shop with documented operation and recovery.

**Human acceptance**
- [ ] Owner performs everyday CMS tasks independently.
- [ ] Customer journey works end to end on agreed devices.
- [ ] Separately authorized live-payment verification succeeds.
- [ ] Orders and communications reach the correct places.
- [ ] Restore and rollback procedures have evidence, not only intentions.
- [ ] No launch-blocking issues remain.
- [ ] Both parties approve the identified release before deployment.
- [ ] Production smoke checks pass and the changelog matches the release.

**Done when:** production verification passes and both final signoffs are recorded.

## Phase 12 — Ongoing improvements

**Purpose:** improve the shop without uncontrolled scope or folder growth.

Select approved wishlist items and give each iteration the same kickoff, GO, review, checks, dual signoff, merge, and deployment process. Potential iterations include seasonal skins, additional machine types, mystery products, one-of-one drops, and new collections.

**Human acceptance**
- [ ] The release delivers the agreed improvement without breaking existing shopping.
- [ ] Completed wishlist entries remain in place, crossed out with release references.
- [ ] New ideas are appended at the bottom rather than silently implemented.

**Done when:** the specific iteration passes its acceptance criteria and both parties sign off. This phase is recurring, not permission for indefinite autonomous development.

## Outstanding decisions and sequencing

- First launch: store only, store plus one machine, or full immersive experience.
- First machine: chosen product, physical mystery selection, or both.
- Exact visual direction and supplied asset treatment.
- Final stack, operational budget, fulfillment rules, and hosting choices.
- Local setup delivery method and approved child-folder structure.
- Which original assets should be tracked versus stored and backed up elsewhere.

Phase numbering is the proposed order. Dependencies and the approved launch scope may justify reordering, but record and approve that change first. For example, customer communication may need to move earlier if it is required before machine development. Do not interpret a later phase number as permission to omit a launch requirement.

## Initial research references

These are evaluation leads only; recheck current terms and documentation during Phase 3.

- Payload ecommerce: https://payloadcms.com/docs/ecommerce/overview
- Medusa admin: https://medusajs.com/admin
- Supabase pricing: https://supabase.com/pricing
- Motion: https://motion.dev/docs/react
- React Three Fiber: https://r3f.docs.pmnd.rs/getting-started/introduction

#### Phase 0 commit and publication record — 2026-11-03

- Amendment GO: on 2026-11-03 the user approved committing the planning documents plus the three mockup HTML pages, and authorized pushing the branch. This supersedes the earlier "no staging, commits, or pushes" note for this limited scope only.
- Approved scope: one local commit of the seven planning documents, `.gitignore`, and the mockup HTML; push of branch `phase-0` to `origin`.
- Still not authorized: merging, deployment, and publication of any artwork or mockup media.
- Review target: commit 2a79201 (10 files, text only, 947 changed lines).
- Excluded by explicit decision: `mockups/homepage-directions/assets/` (24 MB of PNG and MP4) and `mockups/homepage-directions.zip` (32 MB). New ignore rules hold them locally; they remain unpublished.
- Ignore verification: `git check-ignore` resolves the zip, the mockup media, `.DS_Store`, `LOCAL-SECRETS/`, and `.env` to explicit `.gitignore` rules. The staged list contained no secret, binary, or artwork file.
- Known limitation: because the mockup media is unpublished, the committed mockup pages do not render their images when viewed on GitHub.
- Remote state before push: the GitHub repository existed as a public empty repository with no refs. The push created its first content as branch `phase-0` at `307ff59`.
- Default branch: GitHub set `phase-0` as the repository default, because the first branch pushed into an empty repository becomes the default. No `main` branch exists yet. Which branch should be the long-lived reviewed line is an open decision for the user.
- Technical checks: staged file list reviewed before commit; only the checks printed above were run. No browser or runtime verification applies to planning documents.
- Phase status: unchanged. Phase 0 remains complete for its original local-only scope; Phase 1 and Phase 2 remain in progress and require their own briefs and GOs.
