# Pageant Tabulation (React + TS + Tailwind + Supabase)
1. Supabase project → SQL Editor → run `supabase/schema.sql`.
2. Then run `supabase/migration_2.sql` and then `supabase/migration_3.sql` (reports, awards, tie-breakers, finalize, audit, criteria locking, judged awards).
3. Auth → Providers → Email: enable; disable public sign-ups (Auth → Settings).
4. First admin: Auth → Users → Add user (auto-confirm), then SQL:
   `insert into profiles(id,full_name,role) values('<user uuid>','Administrator','admin');`
5. Deploy edge function (needed to create judges; keeps the service role key server-side):
   `supabase functions deploy create-judge`
6. `cp .env.example .env`, fill VITE_SUPABASE_URL / VITE_SUPABASE_ANON_KEY (anon key only).
7. `npm install && npm run dev`. Vercel: import repo, add the two env vars, deploy (vercel.json handles routing).
