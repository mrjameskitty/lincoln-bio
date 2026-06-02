# Lincoln Bio

A free, self-hosted link page template: your own alternative to Linktree and similar services. One HTML file, no account, no tracking, no one harvesting your content.

Built for artists and creators who want to own their own corner of the web.

---

## Before You Start: The 8 Edits

Everything you *need* to change lives behind a numbered `★★★★★ EDIT` marker in `lincoln-bio.html`. Open the file in a text editor, work through these eight in order, and you're done. (Only Edits 6 and 7 are required to actually have links: the rest are identity and labeling.)

### Edit 1: Titles & description

Three lines near the top of the file:

```html
<title>Lincoln Bio</title>
<meta property="og:title"    content="Lincoln Bio" />
<meta property="og:description" content="All my links in one place." />
```

- **`<title>`**: the page title shown in the browser tab.
- **`og:title`**: the title shown when your page is shared on social media.
- **`og:description`**: the blurb shown under that title in a social share.

### Edit 2 (Optional): Social share image

```html
<!-- <meta property="og:image" content="https://yourdomain.com/og.png" /> -->
```

The preview image that appears when your page is shared. This should be a wide image (ideally **1200×630px**), *not* your square avatar. Replace the URL with a full link to your uploaded image, then remove the surrounding comment markers to switch it on.

### Edit 3: Your photo

```html
<img id="avatar" src="avatar.png" alt="Lincoln Bio profile photo">
```

- Replace **`avatar.png`** with your image's filename (keep it in the same folder as the HTML). Use a **square** image: 512×512px or larger is ideal.
- Change the **`alt`** text to your name. This is what screen readers announce.

### Edit 4: Your name (the banner ribbon)

```html
<span id="banner-name">Lincoln Bio</span>
```

Replace `Lincoln Bio` with your name. The ribbon grows to fit. Note that a very long name will push the ribbon beyond the width of the card.

### Edit 5: Your tagline

```html
<p id="tagline">Your tagline or short bio goes here.</p>
```

Replace the text with your own. Don't want a tagline? Delete the whole `<p>` line.

### Edit 6: Featured icons

The quick-access icon row near the top of the page. Pick the platforms you want, uncomment them, and fill in your URLs. Aim for up to six.

### Edit 7: The link list

The main column of buttons. Uncomment the platforms you want, then fill in both the **URL** and the **display text**. To reorder, cut and paste a whole `<li>...</li>` block to its new spot.

### Edit 8: Copyright

```html
&copy;2026 Lincoln Bio &bull; Made with Lincoln Bio
```

Change the first `Lincoln Bio` to your name, and bump the year each January. (Leaving "Made with Lincoln Bio" is the friendly nod: see the license below.)

---

## How These Edits Work

Two patterns cover all eight edits:

**Changing text.** Find the text between an opening tag and its closing tag (for example, between `<title>` and `</title>`) and type over it. Don't touch the tags themselves.

**Activating a link.** Links start *commented out*, which hides them. A comment is anything wrapped in an opening `<!--` marker and a closing `-->` marker. Delete the opening marker before a block and the closing marker after it, and the link goes live. Then replace the placeholder URL inside `href="..."` with your real one.

For example, turning this:

```html
<!-- <li><a class="instagram"
         href="https://www.instagram.com/YOURUSERNAME/"
         target="_blank" rel="noopener">Instagram</a></li> -->
```

into this:

```html
<li><a class="instagram"
         href="https://www.instagram.com/mrjameskitty/"
         target="_blank" rel="noopener">Instagram</a></li>
```

If any of the tag names or attributes are unfamiliar, the **HTML Tag Reference** at the end of this file explains every one used in the template.

---

## Adding a Platform That Isn't Listed

The template ships with icons for most major platforms, but adding your own is two steps.

1. **Add the link.** Copy any existing `<li>` block and change its `class` to a name of your choosing (for example, `class="mysite"`). Update the `href` and display text.

2. **Add the icon.** In the `<style>` block, find the `PLATFORM ICONS` section and add a rule matching your class:

   ```css
   a.mysite::before {
     background-image: url("data:image/svg+xml,...");
   }
   ```

   For icon artwork, use [Simple Icons](https://simpleicons.org): the icons are CC0 (free to use). Open an icon, copy its SVG path, and drop it into the same data-URL format the other icons use. Set the fill to `%23111` (black) so it matches; the link list flips it to white automatically.

---

## Customizing Colors

Every color, size, and spacing value lives in the `:root` block at the top of the `<style>` section as a **CSS variable**. Change the value once and it updates everywhere it's used. You don't need to read the rest of the CSS.

```css
:root {
  --card-bg:       #e9e9e9;  /* card background         */
  --link-bg:       #45a4da;  /* link button color       */
  --link-hover:    #036392;  /* link button on hover    */
  --banner-fill:   #fefefe;  /* ribbon background        */
  --banner-stroke: #cccccc;  /* ribbon outline           */
}
```

The avatar frame is set separately via `--avatar-border` (e.g. `3px solid #ccc`).

Colors are hex values (`#rrggbb`). Any color picker, like the one at [htmlcolorcodes.com](https://htmlcolorcodes.com), gives you a hex code to paste in.

---

## HTML Tag Reference

A short primer on the tags and attributes used in this template. You don't need to memorize these: just refer back when an edit mentions one.

**Tags.** HTML is built from tags that come in pairs: an opening tag like `<a>` and a closing tag like `</a>`. Whatever sits between them is the content. `<a href="https://example.com">Click here</a>` makes a link that reads "Click here."

**Attributes.** Extra settings inside an opening tag, written as `name="value"`:

- **`href`**: the destination URL of a link.
- **`src`**: the source filename of an image.
- **`alt`**: text description of an image, read aloud by screen readers.
- **`class`**: connects an element to its CSS styling (here, it also wires up the platform icon).
- **`id`**: a unique name for one specific element (e.g. `banner-name`, `tagline`).
- **`target="_blank"`**: opens the link in a new browser tab.
- **`rel="noopener"`**: a security best practice for links that open new tabs. Leave it as-is.
- **`aria-label`**: gives icon-only buttons a spoken description for screen readers.

**The tags in this file.**

- **`<title>`**: page title in the browser tab.
- **`<meta>`**: page metadata, including the social-share title, description, and image.
- **`<img>`**: an image (your avatar).
- **`<span>`**: a small inline text container (your name in the ribbon).
- **`<p>`**: a paragraph (your tagline, the copyright line).
- **`<ul>` / `<li>`**: an unordered list and its list items (the link column).
- **`<a>`**: a link (every button).
- **`<div>`**: a generic container used to group sections.
- **`<footer>`**: the bottom section, holding the copyright.

**Comments.** Anything between an opening `<!--` and a closing `-->` is ignored by the browser and invisible on the page. The template uses comments to keep inactive links out of the way until you switch them on.

---

## License

Lincoln Bio is released under **CC BY-NC 4.0**. Full text: [CC-BY-NC-4.0 License.txt](https://github.com/mrjameskitty/lincoln-bio/blob/main/CC-BY-NC-4.0%20License.txt).

You're free to use, modify, and share it (for personal pages, organization pages, and client work) as long as you don't sell the template itself or derivatives of it. Attribution is appreciated; keeping the "Made with Lincoln Bio" footer line does the job nicely, though you're on the honor system.

---

*Lincoln Bio was built as a free alternative for artists looking to own their own link page.*
