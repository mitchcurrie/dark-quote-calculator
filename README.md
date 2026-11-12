# DARK Quote Calculator

A one-page calculator for DARK Plumbing & Gas. Type in the quote total, labour hours and job costs, and it shows the GP straight away. It works on any phone and needs no app store.

## How the GP is worked out

Type every price **including GST**. The calculator takes the GST off before working out GP:

```
Quote ex GST = Quote Total ÷ 1.1
Job cost     = (Labour Hours × $130) + (all other costs ÷ 1.1)
GP $         = Quote ex GST − Job cost
GP %         = GP $ ÷ Quote ex GST
```

- **$130** is the break-even per labour hour (updated 12 Nov 2026). It covers wages, super, leave, vehicles, tools and overheads, so the GP shown is what the business keeps from the job.
- The result matches what you're left with after paying the ATO the net GST on your BAS.
- Green means 30% GP or better, amber means under 30%, and red means the job loses money.
- Before a quote total is typed, the bottom line shows the **quote price needed to hit 40% GP**: Job cost ÷ 0.6 × 1.1, inc GST. Change `TARGET_PCT` in `index.html` to aim for a different GP.

Example: a $1,012 quote with 2.5 hours and $330 of materials gives $358.60 GP (38.98%).

## Put it on GitHub (no coding needed)

1. Sign in at [github.com](https://github.com), then click **+** (top right) and choose **New repository**.
2. Name it, for example `quote-calculator`. Choose **Public** (see the privacy note below), then click **Create repository**.
3. Click **uploading an existing file**. Drag in all the files from this folder: `index.html`, `manifest.webmanifest`, `icon-180.png`, `icon-192.png`, `icon-512.png` and `README.md`. Then click **Commit changes**.
4. Go to **Settings → Pages**. Under **Branch**, choose `main` and `/ (root)`, then click **Save**.
5. Wait a minute or two and refresh. GitHub shows your link, which looks like `https://YOUR-USERNAME.github.io/quote-calculator/`.

Send that link to anyone who needs it.

## Put it on your phone's home screen

- **iPhone:** open the link in Safari, tap **Share**, then **Add to Home Screen**.
- **Android:** open the link in Chrome, tap **⋮**, then **Add to Home screen** (or **Install app**).

It opens full screen with the DARK icon, like an app.

## Change the numbers

Open `index.html` on GitHub, click the pencil icon, and find this block near the bottom:

```js
const BREAK_EVEN = 130;
const GOAL_PCT   = 30;
const GST_PCT    = 10;
```

Change the number, click **Commit changes**, and the live page updates within a minute or two. If you rework the Rates Calculator spreadsheet, put its new break-even rate here.

## Lock code

The calculator opens on a keypad and needs a 4-digit code. Once it's unlocked, it stays open until the app or browser tab is closed, or someone taps **Lock**. After 5 wrong tries, the keypad waits 30 seconds.

The code isn't written in the page. Only its SHA-256 fingerprint is stored, in `CODE_SHA256` near the bottom of `index.html`. To change the code:

1. On a Mac, open Terminal and run `printf '1234' | shasum -a 256`, putting your new code in place of `1234`.
2. Copy the long string of letters and numbers it prints (not the `-` at the end).
3. On GitHub, edit `index.html`, paste it over the old `CODE_SHA256` value, and commit.

The lock keeps casual people out, such as a customer who sees the link. It isn't strong security: the repository is public, so someone technical could read the page's code here on GitHub or work out a 4-digit code.

## Privacy

- Free GitHub accounts can only publish Pages from a **public** repository. Anyone who finds the repo or the link can see the page, including the $130 break-even rate.
- The page tells Google not to list it, so people only find it if they're given the link.
- Nothing typed into the calculator leaves the phone. The last numbers are kept in that phone's browser so they're still there when it reopens, until someone taps **Clear**.
- If you need the code hidden, a paid GitHub plan can publish Pages from a private repository.
