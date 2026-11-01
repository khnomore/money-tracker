# My Money Tracker

A single-page app to track daily expenses, salary and other income, with a dashboard, filters, and CSV import/export. No server, no sign-up, no build step.

## What it does

- Add an entry in a few seconds: type (Expense, Salary, Other income), date, category, amount, optional note
- Dashboard for the selected month: income, expenses, balance, percent saved, spending-by-category chart, daily spending chart
- Filter by month, type, category, or search text
- Edit or delete any entry
- Export the filtered view to CSV (opens in Excel or Google Sheets)
- Import a CSV, or restore a JSON backup
- Loans: enter what you owe, the yearly interest and required monthly payment, then get a payoff plan based on your real income and spending
- Passcode lock with encrypted data, auto-lock and lockout after wrong tries (see Security)
- Change the currency label (default AED)
- Light and dark mode

## Loans and payoff plan

1. In **Loans and payoff plan**, add each loan: name, amount still owed, yearly interest % (0 if none) and the required monthly payment.
2. The app averages your last 3 months of income and non-loan spending to find your **free cash** each month.
3. It suggests putting 50% of free cash toward loans (never less than your required payments). Type your own amount in **Monthly amount I can put toward loans** to override it.
4. You see how many months it takes, the finish month, and the estimated interest. Extra money goes to the highest-interest loan first.
5. Enter a goal in **debt-free in (months)** to see the monthly payment needed.
6. When you pay, click **Record payment** on the loan. The balance drops and the payment is added as a "Loan payment" expense, so your dashboard stays accurate.

The plan is an estimate. Banks may calculate interest differently, so check against your loan statement.

## Security

**What the app does**
- First launch asks you to create a passcode (8+ characters). Your entries and loans are then stored **encrypted** (AES-256-GCM, key made from your passcode with PBKDF2, 310,000 rounds). Without the passcode the saved data is unreadable.
- The app locks itself after 2 minutes without use, and when you switch away from it for more than 30 seconds. **Lock now** locks it immediately.
- After 5 wrong passcodes it makes you wait, and the wait grows with each further failure.
- **Change passcode** is in the top bar. Data saved before you added the passcode is encrypted automatically on first setup.
- The page asks browsers not to send referrers or let scripts talk to other sites.

**Limits you should know**
- GitHub Pages is a public static website. Anyone with the link can load the *app*, but they cannot see *your data*, which lives only in your browser and is encrypted. There is no server-side login.
- **If you forget the passcode, the data cannot be recovered.** "Forgot passcode" erases it so you can start again, then restore from a backup.
- CSV and JSON exports are **not encrypted**. Keep them private and never commit them to GitHub.
- A long passcode matters. A short numeric PIN can be guessed offline by someone who copies your browser data. Use a phrase of 8+ characters.
- Also use your phone's screen lock. The app lock does not replace it.

**Want the page itself to require a login?**
Put the site behind an access gate, for example Cloudflare Access (free for small teams) in front of a Cloudflare Pages deployment, or a private GitHub repo with a paid plan. Only then can people you haven't approved be stopped from loading the app at all.

## Where your data lives

Data is saved, encrypted, in your browser's localStorage on the device you use. It is private to you, but it is not synced between devices and is lost if you clear browser data. Use **Backup (JSON)** regularly, and **Import CSV** to move data to another device.

## Run it locally

Double-click `index.html`. That's all.

## Host it free on GitHub Pages

### 1. Create the repository
1. Sign in at github.com (create a free account if needed).
2. Click **+ > New repository**.
3. Name it `money-tracker`. Choose **Public** (free GitHub Pages needs Public on free accounts).
4. Tick **Add a README file** only if you plan to replace it; otherwise leave unticked. Click **Create repository**.

### 2. Upload the files (no Git needed)
1. In the repo, click **Add file > Upload files**.
2. Drag in `index.html` and `README.md`.
3. Click **Commit changes**.

### 3. Turn on Pages
1. Go to **Settings > Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Choose branch **main** and folder **/ (root)**, then **Save**.
4. Wait 1 to 2 minutes. Your app will be at:
   `https://YOUR-USERNAME.github.io/money-tracker/`

### 4. Add it to your phone's home screen
- iPhone (Safari): Share > **Add to Home Screen**
- Android (Chrome): Menu > **Add to Home screen**

## Using Git instead (optional)

```bash
git init
git add index.html README.md
git commit -m "Add money tracker"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/money-tracker.git
git push -u origin main
```

Then do step 3 above.

## Updating the app later

Edit `index.html` on GitHub (pencil icon) or push a new commit. Pages redeploys automatically. Your saved data stays, because it is stored in your browser, not in the repo.

## Privacy note

Because the repo is public, **anyone can see the code but never your entries**. Your entries stay in your browser. Do not commit exported CSV or JSON files to the repo.

## CSV format

```
Date,Type,Category,Amount,Note
2026-11-01,salary,Salary,15000,October pay
2026-11-02,expense,Groceries,180.50,Weekly shop
```

Type must be `expense`, `salary` or `income`. Dates use `YYYY-MM-DD`.

## Customising

- Categories: edit the `CATS` list near the top of the script in `index.html`.
- Default currency: change `cur:"AED"` in the `S` object.

## Troubleshooting

- **Page shows 404**: wait a couple of minutes after enabling Pages, and confirm the file is named exactly `index.html` in the repo root.
- **Data missing**: you are on a different browser, device, or a private window. Import your backup.
