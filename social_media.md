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
````

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

Planned values:

* `profile` – profile / bio / about / sidebar links (current focus)
* `video` – YouTube video descriptions, pinned comments (future)
* `post` – TikTok/Instagram/Reddit post bodies (future)
* `comment` – comments with links (future)

**Right now we only use**:

```text
utm_medium=profile
```

for profile/about/sidebar links.

---

### 2.3 `utm_campaign`

Use this to say **what the link is about**:

Long-term campaigns:

* `evergreen_website` – links to the main site
* `evergreen_shop` – links to the shop / ranks

Later we can add event campaigns if we ever link directly to event landing pages from socials.

**Rule:** don’t invent random names. Be specific and careful.

---

### 2.4 `utm_content`

This is **where exactly the link lives** on that platform.

Pattern:

```text
utm_content=<platform>_<surface>[_extra]
```

Where:

* `<platform>` – `youtube`, `tiktok`, `instagram`, `reddit`, etc.
* `<surface>` – `profile-main`, `subreddit-sidebar`, etc.
* `[_extra]` – optional extra detail if needed.

Examples (general rules):

* Main website link on YouTube channel → `youtube_profile-main`
* Main website link on TikTok profile → `tiktok_profile-main`
* Main website link on Instagram profile → `instagram_profile-main`
* Main website link on subreddit sidebar → `reddit_subreddit-sidebar`
* Shop link on subreddit sidebar → `reddit_subreddit-sidebar-shop`

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
&utm_content=<platform>_<surface>
&lang=<en|es|ru>
```

Examples of `<path>`:

* main website: `""` (just `/`)
* shop: `shop`

---

## 4. Current social media links using UTMs (Reddit only)

For now, only **Reddit** uses full UTM links, because Reddit hides the query string in the UI.

When you change a link on Reddit, **do not change the UTM parameters** unless you’re intentionally changing tracking.

---

### 4.1 Subreddit – main website link

```text
https://www.6b6t.org/?utm_source=reddit&utm_medium=profile&utm_campaign=evergreen_website&utm_content=reddit_subreddit-sidebar&lang=en
```

Use this as the **main website link** in the subreddit sidebar / community links.

---

### 4.2 Subreddit – shop link

```text
https://www.6b6t.org/shop?utm_source=reddit&utm_medium=profile&utm_campaign=evergreen_shop&utm_content=reddit_subreddit-sidebar-shop&lang=en
```

Use this as the **shop / ranks link** in the subreddit sidebar / community links.

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
2. Decide the **surface** → for profile/bio/sidebar use `utm_medium=profile`.
3. Decide the **goal** → pick `utm_campaign`:

   * website → `evergreen_website`
   * shop → `evergreen_shop`
4. Define **where exactly** it lives → `utm_content=<platform>_<surface>`.
5. Add `lang=<code>` if you know the language.
6. Keep the pattern consistent with this file.

If in doubt, copy the Reddit examples and only change:

* the **platform** in `utm_source`
* the **surface** in `utm_content`
* the **path** (`/` or `/shop`)
* the **lang`** (for non-English accounts)
