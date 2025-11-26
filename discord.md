# 6b6t – Discord UTM Link Guidelines

This document explains **how to build UTM links for anything on the 6b6t Discord** (channels + bot commands) so we can track where rank / website / vote traffic is coming from.

Use this file whenever you add or edit a link on Discord.

> ⚠️ IMPORTANT: Always use `https://www.6b6t.org` (with `www`) in all UTM links.  
> Do **not** use `https://6b6t.org` without `www` for Discord tracking links.

---

## 1. UTM basics for Discord

All Discord links to **6b6t websites** must include these parameters:

```text
utm_source   = discord
utm_medium   = discord_channel | discord_command
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
utm_source=discord
```

---

### 2.2 `utm_medium`

* Messages in channels (text channels, bot messages in channels):

```text
utm_medium=discord_channel
```

* Discord bot commands (e.g. `/shop`):

```text
utm_medium=discord_command
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
* `event_buildcomp_2025`
* `event_christmas_2025`
* etc.

**Rule:** don’t invent random names. Be specific and careful.

---

### 2.4 `utm_content`

This is **where exactly the link lives**.

#### For channels

Pattern:

```text
utm_content=<channel-short>_<slot>
```

Where:

* `<channel-short>`:

  * `about`
  * `updates`
  * `changelog`
  * `merch`
  * `shop`
  * `discordinfo`
  * `advertising`
  * `general`
  * `thankyou`
* `<slot>`:

  * `main` – main link in the message
  * `footer` – footer link in the same message
  * `bot` – when the link is in a bot message that’s always at bottom
  * `faq-q1`, `faq-q2` – specific FAQ entries
  * `bot-vote-reminder` – vote reminder in #general
    (you can add more slots if needed, but keep them short and clear)

Examples:

* Main link in `#shop` → `utm_content=shop_main`
* “Read details at the shop” in `#shop` → `utm_content=shop_footer`
* Vote reminder in `#general` → `utm_content=general_bot-vote-reminder`
* FAQ Q1 link in `#discord-info` → `utm_content=discordinfo_faq-q1`

#### For commands

Pattern:

```text
utm_content=<command-name>
```

Example:

* `/shop` command → `utm_content=shop`

---

### 2.5 `lang`

Language code of the content:

* current English channels/commands: `lang=en`
* later:

  * Spanish channels: `lang=es`
  * Russian channels: `lang=ru`
  * etc.

**Rule:**

* Only set `lang` when you **know** the language.
* For now on the main (English) server: `lang=en`.

---

## 3. URL templates

### 3.1 Channels – generic template

```text
https://www.6b6t.org/<path>
?utm_source=discord
&utm_medium=discord_channel
&utm_campaign=<evergreen_* or event_*>
&utm_content=<channel-short>_<slot>
&lang=<en|es|ru>
```

Examples of `<path>`:

* main website: `""` (just `/`)
* shop: `shop`
* vote: `vote`

---

### 3.2 Commands – generic template

```text
https://www.6b6t.org/<path>
?utm_source=discord
&utm_medium=discord_command
&utm_campaign=<evergreen_* or event_*>
&utm_content=<command-name>
&lang=<en|es|ru>
```

Example:

* `/shop` command → `<command-name>` = `shop`

---

## 4. Current Discord links (EN server)

This is the **current reference list** for the English Discord.

When you change a message, **do not change the UTM parameters** unless you’re intentionally changing tracking.

---

### 4.1 `#about`

**Website link**

```text
https://www.6b6t.org/?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_website&utm_content=about_main&lang=en
```

---

### 4.2 `#updates`

**Event example: Dropping Heads**

* Note: these weren't used, it's a plan for the future:
* In the main paragraph:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=event_dropping_heads_2025&utm_content=updates_main&lang=en
```

* Footer “Our Shop” link:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=event_dropping_heads_2025&utm_content=updates_footer&lang=en
```

For future events, reuse the same `utm_content` but change `utm_campaign` to the new event.

---

### 4.3 `#change-log`

Footer shop CTA:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=changelog_footer&lang=en
```

---

### 4.4 `#6b6t-merch`

Bot message at the bottom:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=merch_bot&lang=en
```

---

### 4.5 `#shop`

Main “support 6b6t” line:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=shop_main&lang=en
```

“Read the details at the 6b6t Shop”:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=shop_footer&lang=en
```

---

### 4.6 `#discord-info`

**FAQ 1 – “Buy it here” (shop):**

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=discordinfo_faq-q1&lang=en
```

**FAQ 3 – “from the 6b6t shop”:**

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=discordinfo_faq-q3&lang=en
```

**“Buy ranks” line in NEW FEATURE section:**

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=discordinfo_newfeature&lang=en
```

---

### 4.7 `#advertising`

Bot message at the bottom:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=advertising_bot&lang=en
```

---

### 4.8 `#general`

Vote reminder (every 12h):

```text
https://www.6b6t.org/vote?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_vote&utm_content=general_bot-vote-reminder&lang=en
```

---

### 4.9 `#thank-you-for-support`

Upsell for existing buyers:

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_channel&utm_campaign=evergreen_shop&utm_content=thankyou_main&lang=en
```

---

## 5. Discord bot command: `/shop`

This is the **Discord bot** command (not Minecraft):

```text
https://www.6b6t.org/shop?utm_source=discord&utm_medium=discord_command&utm_campaign=evergreen_shop&utm_content=shop&lang=en
```

---

## 6. How to add new Discord links

1. Decide the **goal** → pick `utm_campaign`:

   * shop, website, vote, blog, or specific event.
2. Identify **where** the link is:

   * channel? → `utm_medium=discord_channel` and `utm_content=<channel-short>_<slot>`
   * command? → `utm_medium=discord_command` and `utm_content=<command-name>`
3. Add `lang=<code>` if you know the language.
4. Keep the pattern consistent with this file.

If in doubt, copy an existing link from this doc and only change:

* the **path** (`/`, `/shop`, `/vote`)
* the **campaign** (if it’s a new event)
* the **content** (if it’s a new placement)
* the **lang** (for new language channels)

---

You can drop this whole thing into `docs/discord.md` (or similar) and point staff/devs there whenever they touch Discord links.
