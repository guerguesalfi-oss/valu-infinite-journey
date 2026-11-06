# VALU — THE INFINITE JOURNEY

A responsive, Spanish-language birthday experience built with plain HTML, CSS, and JavaScript.

## Files
- `index.html` — page structure and content
- `styles.css` — visual design and responsive layouts
- `script.js` — chapter navigation, interactions, optional message submission
- `config.js` — optional Supabase connection settings
- `supabase.sql` — table and insert-only policy for the optional message form

## Run locally
Open `index.html` in a modern browser. For best results, use a local static server (for example, VS Code Live Server).

## Publish with GitHub Pages
1. Create a GitHub repository and upload the contents of this folder (keep the files in the repository root).
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select `main` and `/ (root)`, then Save.
5. Wait for GitHub Pages to publish the site and open the URL shown there.

## Connect the optional birthday message form (Supabase)
The site works without Supabase, but the final message form will not save responses until it is connected.

1. Create a Supabase project.
2. Open **SQL Editor** and run all of `supabase.sql`.
3. Open **Project Settings → API** (or **Data API**, depending on the dashboard layout) and copy the Project URL and the `anon` / publishable public key.
4. Paste them into `config.js`:

```js
window.VALU_CONFIG = {
  supabaseUrl: "https://YOUR-PROJECT.supabase.co",
  supabaseAnonKey: "YOUR_PUBLIC_ANON_OR_PUBLISHABLE_KEY"
};
```

5. Commit and push the updated `config.js` to GitHub.
6. Test a message using the public site. Submitted messages will appear in Supabase **Table Editor → valu_messages**.

Security notes:
- Use only the public `anon` / publishable key in this static website.
- Never put a `service_role` or secret key in browser code.
- The SQL enables public inserts with length limits and does not enable public reads. Only view submissions from the Supabase dashboard.
- Supabase does not automatically email you when a message arrives. Email alerts require a separate Edge Function/notification setup.

## Before sending the link
- Replace any wording you want to personalize in `index.html` and `script.js`.
- Test the full site on a phone and desktop.
- Test the form only after Supabase is connected.
- Confirm the final public URL and that no draft/test messages remain in the table.

## Notes
- The site uses Google Fonts when internet access is available; fallback fonts are included.
- The music button plays a tiny generated tone only; it does not reproduce any copyrighted song.
- No visitor analytics or identity tracking is included.
