# Repository Guidelines

## Project and assets

Rest and Render is a planned single-owner sticker and greeting card shop. The user owns its visual and creative decisions. Suggest better alternatives with reasons and tradeoffs; obtain approval before changing the creative direction. No application stack or storefront has been selected or implemented.

`ART/` contains product originals; `Assets/` holds general site artwork; `1997 Vending dreams/` holds 1990s machine assets. Preserve these folders and their contents. They are tracked in this public repository: the artwork publication hold was lifted by the owner on 2026-11-03, and the earlier hold came from a previous agent rather than the owner. Only credentials, environment files, OS metadata, and archive zips stay local. Because the repository is public, review every staged file before committing. `LOCAL-SECRETS/` contains local credentials: never read, stage, commit, or disclose its contents as part of routine work. Keep folders minimal and purposeful.

## Phase and review rules

Follow `PHASES.md`. Present a phase brief and wait for an explicit GO before implementation. A phase requires technical checks, human review, assistant signoff, and user signoff before it is complete; the next phase needs its own GO. Do not invent user signoff. A phase GO does not by itself authorize pushing, merging, or deployment. Follow the specific authorizations and stop when instructed.

Append wishlist ideas to `WISHLIST.md`. Preserve completed entries and strike them through only after verified production release, with its date and release reference. Record only actual production releases in `CHANGELOG.md`.

## Costs and dependencies

Use free options only. Verify relevant free-plan limits and explain what happens at those limits before recommending a service. If free capacity cannot meet the need, pause and present free alternatives or simplify. Stripe's standard sale-based processing fees are the approved exception: verify current fees and disclose other possible charges before implementation. Paid Stripe add-ons, other paid services, and future paid upgrades require explicit user approval after full cost disclosure. A recommendation is not approval.

Do not adopt major open-source foundations or services without the user's approval. Do not add packages, frameworks, build commands, or testing instructions until actually selected and present.
