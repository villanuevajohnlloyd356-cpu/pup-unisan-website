# PUP-Unisan website (static site + Supabase + Netlify)

Public pages need no login. Admin and faculty sign in at `login.html`; roles are enforced by Supabase RLS and the `manage-faculty` Netlify Function (service key never reaches the browser).

## Setup
1. Create a Supabase project. Run `supabase/migrations/001_init.sql` in the SQL editor.
2. Auth > Users: add your admin user, then run the `insert into profiles ...` line at the bottom of the SQL file with that user's id. In Auth settings, disable public sign-ups.
3. Edit `public/js/config.js`: Supabase URL, anon key, official admission URL, optional hero image.
4. Netlify: deploy this folder (build settings come from `netlify.toml`). Set env vars: `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_ROLE_KEY`.
5. Local testing: `npx netlify dev`.

## Still needed from you (marked as placeholders)
Verified program list and details, PUP mission/vision, campus info/history, contact details, logo, hero photo, official admission URL.
Programs are edited in the Supabase Table Editor (`programs`); set `is_placeholder` to false once verified.

## Not yet tested
Nothing has been run against a live Supabase project. Before launch, test: navigation, program search, Details links, login redirects per role, faculty add/edit/delete, announcement publish/unpublish, and that a faculty user cannot open `admin.html` data.
