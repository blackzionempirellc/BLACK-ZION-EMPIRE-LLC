# KING SHADONN THE GREAT “DAVID” — Website Starter

Official social media website project for Black Zion Empire LLC.

## Features
Next.js 15, Supabase auth, profile setup/editing, global feed, text posts, likes, comments, follows, discover people, post deletion, and user reports. Responsive purple-and-gold styling. This is a development beta, not production-ready social networking infrastructure.

## Existing Supabase compatibility
This application is designed for the six-table schema previously created in the conversation: `profiles`, `posts` with a `content` column, `follows`, `likes`, `comments`, and `reports`. Do not re-run a different starter `schema.sql` over your existing database. Check column names before deployment. The app explicitly creates a profile after the first successful sign-in, so it does not require a profile trigger.

## Android upload via Termux (recommended)
1. Install Termux from F-Droid, then `termux-setup-storage` and grant file access.
2. `pkg update && pkg install git unzip -y`
3. Place `king-shadonn-web.zip` in your Android Downloads folder.
4. `mkdir -p ~/king-shadonn-upload && cd ~/king-shadonn-upload`
5. `unzip ~/storage/downloads/king-shadonn-web.zip`
6. Verify: `ls -la king-shadonn-web` and ensure `package.json` and `app` are present.
7. Open your existing private repository in Chrome, and copy its HTTPS URL. In Termux: `git clone https://github.com/YOUR_USERNAME/king-shadonn-social.git` (replace YOUR_USERNAME). GitHub may ask you to authenticate; GitHub account passwords do not work for Git HTTPS pushes. Use GitHub CLI/device login or a scoped GitHub token, and do not share credentials in chat.
8. `cp -r king-shadonn-web/. king-shadonn-social/`
9. `cd king-shadonn-social && git status` and check that `.env` or `.env.local` are NOT staged. The provided package contains only `.env.example`.
10. `git add . && git commit -m "Add KING SHADONN social website" && git push origin HEAD`

If Git asks for identity, configure `git config --global user.name "YOUR NAME"` and `git config --global user.email "YOUR GITHUB EMAIL"` before committing. If your repository already contains conflicting source files, do not overwrite them blindly; inspect the changes first.

## Deploy on Vercel
1. Open https://vercel.com/new and import your private GitHub repository.
2. If the repository contains `package.json` at the root, set Root Directory to `./`; if you intentionally placed the website in a `web` subfolder, set Root Directory to `web`.
3. Framework: Next.js.
4. Add environment variables `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY` from Supabase Project Settings / Connect. Use only the publishable (or legacy anon) key, NEVER service_role/secret keys.
5. Deploy, then in Supabase Authentication > URL Configuration set Site URL to your deployed HTTPS URL and add the relevant callback/redirect URLs as appropriate for your auth settings.
6. Enable email confirmation and configure email delivery before public signup.

## Security and public launch
Existing six-table policies permit broad public reads of posts and profiles, and do not implement blocking. Reports have no moderation dashboard yet. Add rate limiting, spam defenses, content moderation, a privacy policy, terms of service, account deletion, abuse review, secure media upload rules, accessibility checks, backups, and age-appropriate safety controls before opening to the general public. This app displays only the latest 100 posts and 200 profiles; production requires pagination and indexes. Avoid sharing secrets or publishing actual `.env` files.

## Local development
`npm install`, copy `.env.example` to `.env.local`, fill in public project settings, and `npm run dev`. To build: `npm run build`.


## Official founder photographs

The homepage now features three user-provided royal portraits in `public/royal/`:

- `royal-portrait-standing.png` — homepage hero and gallery
- `royal-portrait-throne.png` — gallery
- `royal-portrait-ceremonial.png` — gallery

The photos are served as static assets; no Supabase storage bucket is needed for these three images. Upload the complete project directory to GitHub so `public/royal/` is preserved. Images will appear on Vercel after the new commit is deployed.


## November 2026 feature hub update

Added navigable **Professional Network**, **Kingdom & Ministries**, **Royal Academy**, **Events & Programs**, **Marketplace**, **Membership**, and **Digital Wallet** concept screens. These are clearly labeled roadmap previews and do not collect applications, take payments, create credentials, or represent working services.

Added **Customize profile** studio with four themes, professional headline, skills and links. These settings persist **only in the current browser/device** via localStorage and are not yet public, server-side, or cross-device. The existing Supabase feed, authentication, comments, likes, and follows remain in place.

Before launch: add persistent per-user profile fields in Supabase with RLS; professional and community data models; consent, privacy and moderation; accessibility; real event and marketplace services; and use a properly licensed payment processor with compliance review for any wallet functionality.
