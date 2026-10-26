# wakey — pre-launch teaser

Single-page static site. No build step, no framework — `index.html` is the whole site.

## Run locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.

## Backend

Signups (email + optional phone/WhatsApp) are written directly to Supabase from the
browser via `fetch()` — project `goltxxpjfazehknblwak` ("Fit App" org), table
`public.wakey_waitlist`.

The key embedded in `index.html` is the **anon/public key** — that's meant to be public.
Row Level Security only allows `insert` from anonymous visitors; nobody can read, edit or
delete rows with that key. To read signups, use the Supabase dashboard (Table Editor →
`wakey_waitlist`) or the SQL editor.

## Deploy

Any static host works. Easiest options:

- **Vercel**: `npx vercel` from this folder, or drag the folder into vercel.com/new
- **Netlify**: drag this folder onto app.netlify.com/drop
- **GitHub Pages**: push to a repo, enable Pages on the `main` branch

No environment variables needed — the Supabase URL and anon key are already in `index.html`.
