# 6b6t – Social Media UTM Link Guidelines

This document explains **how to build UTM links for 6b6t social media accounts** (YouTube, TikTok, Instagram, Reddit, etc.) so we can track where traffic to the website and shop is coming from.

Use this file whenever you add or edit a link on any 6b6t social profile.

> ⚠️ Many platforms (YouTube, TikTok, Instagram) show the full URL in bios/descriptions, which looks ugly with UTMs.
> For now, we only use **full UTM links on Reddit**, because Reddit hides them.
> Other platforms will use **pretty redirect URLs** once the dev adds them.

---

## 1. UTM basics for social media

All social media links to **6b6t websites** that use UTMs must include these parameters:

```text
utm_source   = <platform>
utm_medium   = <surface>
utm_campaign = <what this link is for>
utm_content  = <where exactly the link lives>
lang         = <language code> (en, es, ru, …) – only if known
```

We only add UTMs to links that go to our own domains:

* `https://www.6b6t.org`
* `https://www.6b6t.org/shop`

---

## 2. Allowed values

### 2.1 `utm_source`

Platform name in lowercase, for example:

```text
youtube
tiktok
instagram
reddit
```

(If we ever add language-specific accounts, we still keep `utm_source=youtube` / `tiktok` and use `lang` to separate languages.)

---

### 2.2 `utm_medium`

This describes **what type of surface** the link is on.

Allowed values:

* `profile` – profile / bio / about / sidebar links
* `post` – post bodies (Reddit posts; later also other platforms if we ever use full UTMs there)
* `comment` – comments with links (e.g. pinned Reddit comment)
* `video` – YouTube video descriptions / pinned comments (future)

**Right now we actively use:**

```text
utm_medium=profile
```

and on Reddit we also allow `utm_medium=post` and `utm_medium=comment` when we include links in posts/comments.

---

### 2.3 `utm_campaign`

Use this to say **what the link is about**:

Long-term campaigns:

* `evergreen_website` – links to the main site
* `evergreen_shop` – links to the shop / ranks

Event / time-limited campaigns:

* `event_<name>_<year>` (example: `event_newshop_ultrapricechanges_2026`)

**Rules:**

* don’t invent random names. Be specific and careful.
* if you already used an event campaign name on Discord for the same announcement, reuse the same `utm_campaign` on Reddit/socials.

---

### 2.4 `utm_content`

This is **where exactly the link lives** on that platform.

#### Preferred pattern (NEW links)

Use a short, Discord-like placement format:

```text
utm_content=<surface>_<slot>
```

Where:

* `<surface>` – `profile`, `post`, `comment`, `video`
* `<slot>` – short placement identifier, e.g. `main`, `footer`, `pinned`, `sidebar`

Examples (recommended):

* Main shop link inside a Reddit post body → `utm_content=post_main`
* Footer / secondary shop link in the same Reddit post → `utm_content=post_footer`
* Link in a pinned Reddit comment → `utm_content=comment_pinned`
* Link in a normal Reddit comment thread → `utm_content=comment_main`
* Profile/sidebar main website link → `utm_content=profile_sidebar`
* Profile/sidebar shop link → `utm_content=profile_sidebar-shop` (if you need this distinction)

**Rule:** use underscores for new values (avoid `-`).

#### Legacy pattern (already live, do not change)

Some older links already use a different format (including platform prefixes and `-`).
These must remain unchanged to preserve tracking continuity:

* `utm_content=reddit_subreddit-sidebar`
* `utm_content=reddit_subreddit-sidebar-shop`

---

### 2.5 `lang`

Language code of the content/account:

* current English social accounts/subreddit: `lang=en`
* later:

  * Spanish account: `lang=es`
  * Russian account: `lang=ru`
  * etc.

**Rule:**

* Only set `lang` when you **know** the language.
* For now, all live social links in this file use `lang=en`.

---

## 3. URL templates

### 3.1 Profile / about / sidebar – generic template

```text
https://www.6b6t.org/<path>
?utm_source=<platform>
&utm_medium=profile
&utm_campaign=<evergreen_website or evergreen_shop>
&utm_content=<utm_content value>
&lang=<en|es|ru>
```

Examples of `<path>`:

* main website: `""` (just `/`)
* shop: `shop`

---

### 3.2 Posts – generic template (Reddit supported)

```text
https://www.6b6t.org/<path>
?utm_source=<platform>
&utm_medium=post
&utm_campaign=<evergreen_* or event_*>
&utm_content=<utm_content value>
&lang=<en|es|ru>
```

---

### 3.3 Comments – generic template (Reddit supported)

```text
https://www.6b6t.org/<path>
?utm_source=<platform>
&utm_medium=comment
&utm_campaign=<evergreen_* or event_*>
&utm_content=<utm_content value>
&lang=<en|es|ru>
```

---

## 4. Current social media links using UTMs (Reddit only)

For now, only **Reddit** uses full UTM links, because Reddit hides the query string in the UI.

When you change a link on Reddit, **do not change the UTM parameters** unless you’re intentionally changing tracking.

---

### 4.1 Subreddit – main website link (EXISTING – do not change)

```text
https://www.6b6t.org/?utm_source=reddit&utm_medium=profile&utm_campaign=evergreen_website&utm_content=reddit_subreddit-sidebar&lang=en
```

Use this as the **main website link** in the subreddit sidebar / community links.

---

### 4.2 Subreddit – shop link (EXISTING – do not change)

```text
https://www.6b6t.org/shop?utm_source=reddit&utm_medium=profile&utm_campaign=evergreen_shop&utm_content=reddit_subreddit-sidebar-shop&lang=en
```

Use this as the **shop / ranks link** in the subreddit sidebar / community links.

---

### 4.3 Reddit posts (supported)

Use these when you make a Reddit post announcing something and include a link in the post body.

**Event announcement example (shop link in the main paragraph):**

```text
https://www.6b6t.org/shop?utm_source=reddit&utm_medium=post&utm_campaign=event_newshop_ultrapricechanges_2026&utm_content=post_main&lang=en
```

**Same post, footer CTA shop link:**

```text
https://www.6b6t.org/shop?utm_source=reddit&utm_medium=post&utm_campaign=event_newshop_ultrapricechanges_2026&utm_content=post_footer&lang=en
```

**Optional: pinned comment link (if you post the link as a pinned comment instead):**

```text
https://www.6b6t.org/shop?utm_source=reddit&utm_medium=comment&utm_campaign=event_newshop_ultrapricechanges_2026&utm_content=comment_pinned&lang=en
```

**Rules:**

* Only add UTMs to `www.6b6t.org` links.
* Do not add UTMs to external links (Stripe billing portal, YouTube, TikTok, etc.).
* Reuse the same `utm_campaign` across all links within the same Reddit post.

---

## 5. Other platforms (YouTube, TikTok, Instagram)

For now:

* **Do NOT paste full UTM URLs** into YouTube/TikTok/Instagram bios, because they show the entire query string and look bad.
* Use **clean URLs** like `https://www.6b6t.org` until the dev adds pretty redirect paths such as:

  * `/yt` → redirects to UTM’d YouTube URL
  * `/tt` → redirects to UTM’d TikTok URL
  * `/ig` → redirects to UTM’d Instagram URL

Once redirects are ready, we can update this file with the final UTM targets and agreed short paths.

---

## 6. How to add new social links later

1. Decide the **platform** → `utm_source=<platform>`.
2. Decide the **surface** → pick `utm_medium`:

   * profile/bio/sidebar → `utm_medium=profile`
   * post body → `utm_medium=post` (Reddit supported)
   * comment → `utm_medium=comment` (Reddit supported)
3. Decide the **goal** → pick `utm_campaign`:

   * website → `evergreen_website`
   * shop → `evergreen_shop`
   * event announcement → `event_<name>_<year>`
4. Define **where exactly** it lives → set `utm_content`:

   * Preferred new format: `<surface>_<slot>` (example: `post_main`)
   * Keep legacy values unchanged if already live
5. Add `lang=<code>` if you know the language.
6. Keep the pattern consistent with this file.

If in doubt, copy an existing Reddit sidebar link (profile) or the Reddit post examples above (post/comment) and only change:

* the **platform** in `utm_source`
* the **utm_medium** (`profile` vs `post` vs `comment`)
* the **campaign** (if it’s a new event)
* the **content** (if it’s a new placement)
* the **path** (`/` or `/shop`)
* the **lang** (for non-English accounts)
