# index.html — Correction Diffs
# Date: 2026-03-29
# Apply these changes in order using GitHub's web editor (pencil icon on the file).

---

## FIX 1 — Stripe links for EN/ES/PT ebooks
### Find:
```
ebook_en: "coming-soon.html?lang=en&format=ebook", // LINE 797 — EN ebook Stripe link — EN ebook (add link when available)
ebook_es: "coming-soon.html?lang=es&format=ebook", // LINE 798 — ES ebook Stripe link — ES ebook (add link when available)
ebook_pt: "coming-soon.html?lang=pt&format=ebook", // LINE 799 — PT ebook Stripe link — PT ebook (add link when available)
```
### Replace with:
```
ebook_en: "https://buy.stripe.com/dRm14n4Iwag8dZL5djawo0r", // EN ebook pre-order — Stripe
ebook_es: "https://buy.stripe.com/dRm14n4Iwag8dZL5djawo0r", // ES ebook pre-order — Stripe
ebook_pt: "https://buy.stripe.com/dRm14n4Iwag8dZL5djawo0r", // PT ebook pre-order — Stripe
```

---

## FIX 2 — Declare missing --terracotta CSS variable
### Find (inside :root { ... }):
```
  --text-muted: #7a6e60;
}
```
### Replace with:
```
  --text-muted: #7a6e60;
  --terracotta: #8b3a2a;
}
```

---

## FIX 3 — Remove orphan .hero-edition-badge CSS rule
### Find and DELETE this entire block:
```
.hero-edition-badge {
  position: absolute; bottom: 36px; left: 36px; z-index: 3;
  font-size: 0.6rem; letter-spacing: 0.2em; text-transform: uppercase;
  font-family: 'Cinzel', serif; color: var(--saffron);
  border: 1px solid rgba(200,132,58,0.4); padding: 7px 14px;
  background: rgba(15,13,10,0.6); backdrop-filter: blur(4px);
}
```

---

## FIX 4 — Remove orphan .lang-glyph CSS rule
### Find and DELETE this entire block:
```
.lang-glyph {
  font-family: 'Cormorant Garamond', serif; font-size: 2.8rem; font-style: italic;
  font-weight: 600; color: rgba(200,132,58,0.2); margin-bottom: 14px; line-height: 1;
}
```

---

## FIX 5 — Remove orphan .btn-preorder CSS rule
### Find and DELETE this entire block (including the ::after):
```
.btn-preorder {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 12px 26px; border: 1px solid rgba(200,132,58,0.25);
  color: var(--text-muted); font-family: 'Cinzel', serif; font-size: 0.65rem;
  letter-spacing: 0.16em; text-transform: uppercase; cursor: pointer;
  transition: all 0.25s; position: relative;
}
.btn-preorder::after {
  content: 'PRE-ORDER'; position: absolute; top: -10px; right: -4px;
  font-size: 0.45rem; letter-spacing: 0.14em; background: var(--terracotta, #8b3a2a);
  color: var(--parchment); padding: 2px 6px; font-family: 'Cinzel', serif;
}
.btn-preorder:hover { border-color: var(--saffron); color: var(--warm-sand); }
```

---

## FIX 6 — Remove .buy-direct from responsive media query
### Find (inside @media (max-width: 1100px)):
```
  .preview, .shop, .languages, .buy-direct { padding: 80px 48px; }
```
### Replace with:
```
  .preview, .shop, .languages { padding: 80px 48px; }
```

---

## FIX 7 — Dynamic lang attribute on <html>
### Find (in the setLang function in the JS, near bottom of file):
```
function setLang(lang) {
```
### After the opening line of that function, add:
```
  document.documentElement.lang = lang;
```
So it reads:
```
function setLang(lang) {
  document.documentElement.lang = lang;
  // ... rest of existing function
```

---

## FIX 8 — rel="noopener noreferrer" on all target="_blank" links
### These are the links to update. For each one, add  rel="noopener noreferrer"

1. Hero preview button:
   Find:  href="preview-de.html" target="_blank"
   Add:   rel="noopener noreferrer"

2. Preview section open button (id="prev-open-btn"):
   Find:  href="preview-de.html" target="_blank"
   Add:   rel="noopener noreferrer"

3. Audio preview link (if present with target="_blank"):
   Add:   rel="noopener noreferrer"

Note: The Stripe and Thalia buy links open in same tab via JS — no change needed there.
