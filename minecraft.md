# Minecraft server UTM and language conventions

Approved 2026-09-11. This is an intentional migration from legacy source=command, medium=server and campaigns shop/website/commands/vote. Historical data retains its old values. Record the actual deployment time in the rollout evidence.

## Parameters

- `utm_source=minecraft`
- `utm_medium=server_command` for command replies and command-triggered access notices.
- `utm_medium=server_broadcast` reserved for automatic broadcasts (not migrated in this rollout).
- `utm_campaign=evergreen_shop|evergreen_website|evergreen_vote`, or an agreed `event_<name>_<year>`.
- `utm_content` identifies the exact placement; use stable lowercase underscore names.
- `lang` is the actual message language when a supported player language is known. Omit it entirely for missing/unsupported client locale in default mode. Do not label an English fallback as translated.
- `account_type=premium|cracked|bedrock|unknown` is a separate custom parameter, not a UTM campaign. Premium/cracked describe the Java session authentication mode, not rank ownership. Check Floodgate before Java online-mode classification.
- Keep existing functional parameters such as the encoded player username.

Only tag links to https://www.6b6t.org. Do not append UTMs to Discord, Reddit, Telegram, GitHub, CurseForge or other external links. The blog remains excluded.

## Initial placements

| Placement | Campaign | Content |
|---|---|---|
| Help: commands page | evergreen_website | help_commands |
| Shop / Buy: Browse Ranks | evergreen_shop | shop_ranks |
| Shop / Buy: Explore Legend | evergreen_shop | shop_legend |
| Website | evergreen_website | website |
| Account / Link | evergreen_website | account |
| Skin restriction: Browse Ranks | evergreen_shop | skin_requirement_shop |

Aliases share their primary command's placement. Never embed the player's username in utm_content.

## Language

The shared PlayerLanguage service owns /language and UUID-based saved overrides. Default clears the override and follows subsequent Minecraft language changes. Explicit choices override the client. Initial translation targets: en, de, pl, es, tr, fr. Only approved, enabled translations are selectable. Missing translations fall back to English.

Website routing and message attribution are separate. Use supported /<language>/ paths; a lang query parameter alone does not change website routing. The website currently supports en/de/es/pl/tr (also hi/ru outside this plugin rollout); French is not active. Do not create broken /fr links. Unknown locale links omit lang and can use the website's normal language negotiation.

## Example

`https://www.6b6t.org/es/shop?username=Example&utm_source=minecraft&utm_medium=server_command&utm_campaign=evergreen_shop&utm_content=shop_ranks&lang=es&account_type=premium`

Language and account parameters are descriptive analytics inputs, not authentication or authorization. Website analytics must explicitly collect account_type before reports can reliably segment by it; adding the URL parameter alone is not proof of collection.

## Translation handoff

Each integrated plugin keeps messages in messages/<language>.json, with text only. Operational config, destinations, tracking settings and database credentials stay outside these files. Preserve message keys, MiniMessage formatting and placeholders. English is the source; do not publish untranslated templates as completed translations.

Broader broadcasts and website analytics/French implementation remain separate follow-up work.
