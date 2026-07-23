# Dev Account Setup — Dedicated Accounts, No Manual Switching

Wedding Gully uses dedicated Gmail/GitHub/Vercel/Supabase accounts, separate from personal accounts. This doc records how that separation is wired up so nobody has to manually log out/in when moving between this project and others.

## GitHub — SSH host alias (fully automatic)

A dedicated SSH keypair was generated for this project:
- Private key: `~/.ssh/id_ed25519_weddinggully` (no passphrase set — add one later with `ssh-keygen -p -f ~/.ssh/id_ed25519_weddinggully` if desired)
- Public key: `~/.ssh/id_ed25519_weddinggully.pub`

A host alias was added to `~/.ssh/config`:

```
Host github-weddinggully
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_weddinggully
  IdentitiesOnly yes
```

**One-time step (manual, on github.com):** add the public key above to the dedicated GitHub account under Settings → SSH and GPG keys → New SSH key.

**How it's used:** any repo remote added as `git@github-weddinggully:<username>/<repo>.git` (instead of the normal `git@github.com:...`) authenticates through this key automatically — no login/logout, no credential prompt.

A per-folder git identity override was also added via `~/.gitconfig`'s `includeIf "gitdir:"`, so commits made anywhere under `C:/Projects/wedding-gully/` automatically use the dedicated account's name/email instead of the global personal identity — see `.gitconfig-local` in this repo root for the actual values.

**This pattern is reusable** for any future project that needs a different GitHub identity: new SSH key, new host alias, new `includeIf` block pointed at that project's folder.

## Vercel — per-project access token

The Vercel CLI only holds one logged-in session at a time, so instead of switching logins, commands are scoped with a token:

```
vercel --token $VERCEL_TOKEN ...
```

Token lives in `.env.local` (gitignored, see `.env.example` for the shape) generated from the **dedicated** Vercel account's dashboard under Settings → Tokens.

## Supabase — same pattern

Supabase CLI isn't installed yet (not needed until Phase 0 dev setup). When it is, use `SUPABASE_ACCESS_TOKEN` from `.env.local`, generated from the dedicated account's dashboard under Account → Access Tokens — same reasoning as Vercel.

## Status

- [x] SSH key generated and host alias configured
- [ ] Public key added to dedicated GitHub account (manual step, pending)
- [ ] `.gitconfig-local` filled in with dedicated account's name/email (pending — need the dedicated Gmail address)
- [ ] Repo created under dedicated GitHub account and pushed
- [ ] Vercel token generated and added to `.env.local`
- [ ] Supabase CLI installed + token generated (deferred to Phase 0)
