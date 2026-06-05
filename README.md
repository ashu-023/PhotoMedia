**PhotoMedia**


Drop a folder of photos and arrange them in 3D space. Sign in to save spaces and revisit them later.

**Stack**


React 19 + Vite + TypeScript

Three.js (raw — custom render pipeline with SMAA + OutlinePass)

Zustand for state

Supabase (Auth + Postgres) for accounts and saved spaces — photos stay on your device

Vercel for hosting


**Local development**


Clone the repo.

Install: npm install

Create a Supabase project at supabase.com.

In the Supabase SQL editor, run supabase/migrations/0001_init.sql.

Copy .env.example to .env and fill in VITE_SUPABASE_URL and VITE_SUPABASE_ANON_KEY from Supabase → Settings → API.

npm run dev → http://localhost:5173


**Deploy to Vercel**


Push the repo to GitHub.

Import the repo at vercel.com/new.

Set environment variables: VITE_SUPABASE_URL and VITE_SUPABASE_ANON_KEY.

Deploy. Vercel auto-detects Vite and serves the static build.

In Supabase → Authentication → URL Configuration, add your Vercel deployment URL to "Site URL" and "Redirect URLs" so magic links work in production.


**How saved spaces work**


When you drop photos, PinViz hashes the first 64 KB of each file. Saving a space stores those hashes plus your layout in Supabase. Photos themselves never leave your device. To revisit a space, drop the same folder — files are matched by hash, so renamed files still work.
