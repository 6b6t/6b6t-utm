# 6b6t – Telegram UTM Link Guidelines

This document explains **how to build UTM links for anything on the 6b6t Telegram** (group topics now; bots/channels later) so we can track where rank / website / vote traffic is coming from.

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

* `https://www.6b6t.org` (including paths like `/en/stats/...`, `/antispam`, etc.)
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

```text
utm_medium=telegram_group
```

**Future (reserved for consistency):**

```text
utm_medium=telegram_channel
utm_medium=telegram_bot_message
utm_medium=telegram_bot_command
```

---

### 2.3 `utm_campaign`

Use this to say **what the link is about**:

Long-term campaigns:

* `evergreen_website` – general links on the main website (stats pages, info pages, etc.)
* `evergreen_shop` – links to the shop / ranks
* `evergreen_vote` – links to the vote page
* `evergreen_blog` – links to the blog (for now unused)

Event / time-limited campaigns:

* `event_dropping_heads_2025`
* `event_buildcomp_2026`
* `event_christmas_2025`
* etc.

**Rule:** don’t invent random names. Be specific and careful.

---

### 2.4 `utm_content`

This is **where exactly the link lives**.

#### Telegram “space code”

We use a stable short code for the Telegram container:

* `org6b6t` – main 6b6t Telegram group (`t.me/org6b6t`)

#### For group topics (current setup)

Pattern (same idea as Discord’s `<channel-short>_<slot>`, but for Telegram topics):

```text
utm_content=org6b6t_<topic>_<slot>
```

Where:

* `<topic>` (current topics):

  * `news`
  * `general`
* `<slot>`:

  * `main` – main link inside the post
  * `footer` – footer / CTA link inside the same post
  * `pinned` – link in a pinned message in that topic
  * (add more only if needed, keep them short: `button1`, `rules`, `faq-q1`, etc.)

Examples:

* Main link in `news` topic → `utm_content=org6b6t_news_main`
* Footer CTA in `news` topic → `utm_content=org6b6t_news_footer`
* Main link in `General` topic → `utm_content=org6b6t_general_main`
* Pinned message in `news` topic → `utm_content=org6b6t_news_pinned`

---

### 2.5 `lang`

Language code of the content:

* current English Telegram: `lang=en`
* later: `lang=es`, `lang=ru`, etc.

**Rule:**

* Only set `lang` when you **know** the language.
* For now on the main Telegram: `lang=en`.

---

## 3. URL templates

### 3.1 Group topics – generic template (current)

```text
https://www.6b6t.org/<path>
?utm_source=telegram
&utm_medium=telegram_group
&utm_campaign=<evergreen_* or event_*>
&utm_content=org6b6t_<topic>_<slot>
&lang=<en|es|ru>
```

Examples of `<path>`:

* main website: `""` (just `/`)
* shop: `shop`
* vote: `vote`
* stats page: `en/stats/<username>`
* anti-spam page: `antispam`

---

## 4. Current Telegram links (org6b6t)

When you change a message, **do not change the UTM parameters** unless you’re intentionally changing tracking.

### 4.1 Topic: `news`

**Shop link (footer CTA in a news post)**

```text
https://www.6b6t.org/shop?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_shop&utm_content=org6b6t_news_footer&lang=en
```

**Vote link (main link in a news post)**

```text
https://www.6b6t.org/vote?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_vote&utm_content=org6b6t_news_main&lang=en
```

**Website/stats/info link (main link in a news post)**

```text
https://www.6b6t.org/?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_website&utm_content=org6b6t_news_main&lang=en
```

---

### 4.2 Topic: `General`

**Website link (main link in a general post)**

```text
https://www.6b6t.org/?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_website&utm_content=org6b6t_general_main&lang=en
```

**Shop link (main link in a general post)**

```text
https://www.6b6t.org/shop?utm_source=telegram&utm_medium=telegram_group&utm_campaign=evergreen_shop&utm_content=org6b6t_general_main&lang=en
```

---

## 5. How to add new Telegram links

1. Decide the **goal** → pick `utm_campaign`:

   * website, shop, vote, or a specific `event_*`.
2. Identify **where** the link is:

   * topic? → `utm_medium=telegram_group` and `utm_content=org6b6t_<topic>_<slot>`
3. Add `lang=<code>` if you know the language.
4. Keep the pattern consistent with this file.

If in doubt, copy an existing link from this doc and only change:

* the **path** (`/`, `/shop`, `/vote`, `/en/stats/...`, `/antispam`, etc.)
* the **campaign** (if it’s a new event)
* the **topic/slot** inside `utm_content`
* the **lang** (for new languages)
