# Zion Computer Centre Website

Website for Zion Computer Centre, along College of Health Technology, Zawan, Jos South, Plateau State.
Built with Next.js, Tailwind CSS and Supabase. Hosted on Vercel.

Pages: Home, Services, Order (with file upload), Contact, and a private Admin dashboard (`/admin`).

---

## 1. Edit your business details
Open `lib/config.js` and change your **prices**, **opening hours**, phone and address. Save the file.
Everything on the site updates from this one file.

## 2. Set up Supabase (database and login)
1. Go to supabase.com and create a project.
2. Open **SQL Editor > New query**, paste everything from `supabase/schema.sql`, click **Run**.
3. Open **Authentication > Users > Add user**. Enter your email and a strong password. This is your admin login.
4. Open **Authentication** settings and **turn OFF "Allow new users to sign up"**. This stops strangers from creating accounts.
5. Open **Project Settings > API** and copy:
   - **Project URL**
   - **anon public key**
   (Never use or share the `service_role` key.)

## 3. Run it on your computer (optional)
1. Install Node.js (nodejs.org, the LTS version).
2. Copy `.env.example` to `.env.local` and paste your Project URL and anon key.
3. In a terminal inside this folder:
   ```
   npm install
   npm run dev
   ```
4. Open http://localhost:3000

## 4. Push to GitHub
Create an empty repo on github.com named `zion-computer-centre` (no README, no .gitignore). Then:
```
git init
git add .
git commit -m "Zion Computer Centre website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/zion-computer-centre.git
git push -u origin main
```
Replace `YOUR-USERNAME` with your GitHub username. Your `.env.local` file is ignored and is never uploaded.

## 5. Deploy on Vercel
1. In Vercel click **Add New > Project** and import the GitHub repo.
2. Before clicking Deploy, open **Environment Variables** and add:
   - `NEXT_PUBLIC_SUPABASE_URL` = your Project URL
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY` = your anon public key
3. Click **Deploy**. When it finishes, Vercel gives you a live link.
4. Any future change you push to GitHub redeploys the site automatically.

## 6. Test everything
- Place a test order with a PDF or Word file on `/order`.
- Log in at `/admin`, confirm the order appears, change its status and download the file.

## Updating the site later
```
git add .
git commit -m "Describe your change"
git push
```

## Troubleshooting
- **Order fails to send:** check both environment variables in Vercel, then redeploy (Deployments > Redeploy).
- **Admin shows "Could not load orders":** re-run `supabase/schema.sql` and make sure you are logged in.
- **File upload fails:** file must be PDF, DOC or DOCX and under 10MB.
- **Cannot log in:** confirm the user exists under Supabase > Authentication > Users.

## Security notes
- Only the public `anon` key is used. Never commit the `service_role` key.
- Visitors can only submit orders. Only the logged-in admin can read orders and download files.
