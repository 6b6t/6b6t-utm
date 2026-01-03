# 6b6t – Telegram UTM Link Guidelines

This document explains **how to build UTM links for anything on the 6b6t Telegram** (group topics now, bots/channels later) so we can track where rank / website / vote traffic is coming from.

Use this file whenever you add or edit a link on Telegram.

> ⚠️ IMPORTANT: Always use `https://www.6b6t.org` (with `www`) in all UTM links.
> Do **not** use `https://6b6t.org` without `www` for Telegram tracking links.

---

## 1. UTM basics for Telegram

All Telegram links to **6b6t websites** must include these parameters:

```text
utm_source   = telegram
utm_medium   = telegram_group | telegram_channel | telegram_bot_message | telegram_bot_command
utm_campaign = <what this link is for>
utm_content  = <where exactly the link lives>
lang         = <language code> (en, es, ru, …) – only if known
```

We only add UTMs to links that go to our own domains:

* `https://www.6b6t.org`
* `https://www.6b6t.org/shop`
* `https://www.6b6t.org/vote`
* `for now we skip https://blog.6b6t.org as an exception`

---

## 2. Allowed values

### 2.1 `utm_source`

Always:

```text
utm_source=telegram
```

---

### 2.2 `utm_medium`

**Current setup (Telegram group with topics):**

* Messages posted inside the Telegram group (including inside a topic like `news` or `General`):

```text
utm_medium=telegram_group
```

**Future (reserved for consistency):**

* Messages posted in a Telegram channel (broadcast feed):

```text
utm_medium=telegram_channel
```

* Links sent by a bot message (reminders, buttons, automated posts):

```text
utm_medium=telegram_bot_message
```

* Bot commands (e.g. `/shop` in Telegram):

```text
utm_medium=telegram_bot_command
```

---

### 2.3 `utm_campaign`

Use this to say **what the link is about**:

Long-term campaigns:

* `evergreen_website` – links to the main site
* `evergreen_shop` – links to the shop / ranks
* `evergreen_vote` – links to the vote page
* `evergreen_blog` – links to the blog (for now unused)

Event / time-limited campaigns:

* `event_dropping_heads_2025`
* `event_buildcomp_2026`
* `event_christmas_2025`
* etc.

Optional (useful for announcements / changelogs):

* `changelog_YYYY_MM_DD` – when you want to attribute clicks to a specific dated announcement
  Example: `changelog_2026_01_03`

**Rule:** don’t invent random names. Be specific and careful.

---

### 2.4 `utm_content`

This is **where exactly the link lives**.

#### Telegram “space code”

We use a stable short code for the Telegram container to keep tracking consistent even if names change.

Current setup uses:

* `org6b6t` – main 6b6t Telegram group (`t.me/org6b6t`)

#### For group topics (current setup)

Pattern:

```text
utm_content=org6b6t_<topic>_<placement>
```

Where:

* `<topic>` (current topics):

  * `news`
  * `general`
* `<placement>`:

  * `post` – normal message
  * `pinned` – pinned message in that topic
  * (you can add more later: `footer`, `button1`, etc., but keep them short and clear)

Examples:

* Post in `news` topic → `utm_content=org6b6t_news_post`
* Pinned message in `news` topic → `utm_content=org6b6t_news_pinned`
* Post in `General` topic → `utm_content=org6b6t_general_post`
* Pinned message in `General` topic → `utm_content=org6b6t_general_pinned`

#### Future (reserved): for bot commands

Pattern:

```text
utm_content=<command-name>
```

Example:

* `/shop` command → `utm_content=shop`

---

### 2.5 `lang`

Language code of the content:

* current English Telegram: `lang=en`
* later:

  * Spanish Telegram: `lang=es`
  * Russian Telegram: `lang=ru`
  * etc.

**Rule:**

* Only set `lang` when you **know** the language.
* For now on the main Telegram: `lang=en`.

---

## 3. URL templates

### 3.1 Telegram group topics – generic template (current)

```text
https://www.6b6t.org/<path>
?utm_source=telegram
&utm_medium=telegram_group
&utm_campaign=<evergreen_* or event_* or changelog_YYYY_MM_DD>
&utm_content=org6b6t_<topic>_<placement>
&lang=<en|es|ru>
```

Examples of `<path>`:

* main website: `""` (just `/`)
* shop: `shop`
* vote: `vote`

---

### 3.2 Telegram bot commands – generic template (future)

```text
https://www.6b6t.org/<path>
?utm_source=telegram
&utm_medium=telegram_bot_command
&utm_campaign=<evergreen_* or event_*>
&utm_content=<command-name>
&lang=<en|es|ru>
```

---

## 4. Current Telegram links (org6b6t)

This is the **current reference list** for the main Telegram group.

When you change a message, **do not change the UTM parameters** unless you’re intentionally changing tracking.

---

### 4.1 Topic: `news`

**Shop link (announcement post)**

```text
https://www.6b6t.org/shop?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_shop&utm_content=org6b6t_news_post&lang=en
```

**Vote link (announcement post)**

```text
https://www.6b6t.org/vote?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_vote&utm_content=org6b6t_news_post&lang=en
```

**Website link (announcement post)**

```text
https://www.6b6t.org/?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_website&utm_content=org6b6t_news_post&lang=en
```

Optional (per-announcement attribution):

**Changelog-style campaign example (dated announcement)**

```text
https://www.6b6t.org/shop?utm_source=telegram&utm_medium=telegram_group&utm_campaign=changelog_2026_01_03&utm_content=org6b6t_news_post&lang=en
```

---

### 4.2 Topic: `General`

**Website link (normal chat post)**

```text
https://www.6b6t.org/?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_website&utm_content=org6b6t_general_post&lang=en
```

**Shop link (normal chat post)**

```text
https://www.6b6t.org/shop?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_shop&utm_content=org6b6t_general_post&lang=en
```

**Vote link (normal chat post)**

```text
https://www.6b6t.org/vote?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_vote&utm_content=org6b6t_general_post&lang=en
```

---

## 5. How to add new Telegram links

1. Decide the **goal** → pick `utm_campaign`:

   * shop, website, vote, blog, or specific event (or `changelog_YYYY_MM_DD` for dated announcements).
2. Identify **where** the link is:

   * group topic post (current) → `utm_medium=telegram_group` and `utm_content=org6b6t_<topic>_<placement>`
   * (future) channel post → `utm_medium=telegram_channel`
   * (future) bot message → `utm_medium=telegram_bot_message`
   * (future) bot command → `utm_medium=telegram_bot_command`
3. Add `lang=<code>` if you know the language.
4. Keep the pattern consistent with this file.

If in doubt, copy an existing link from this doc and only change:

* the **path** (`/`, `/shop`, `/vote`)
* the **campaign** (if it’s a new event or dated announcement)
* the **topic/placement** inside `utm_content`
* the **lang** (for new language Telegrams)

---
