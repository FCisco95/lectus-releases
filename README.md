# Lectus

> Voice dictation for any app. Hold a key, speak, and your words land in whatever text field you were already in.

**Lectus** (by Organic) is a Whisper-powered dictation app for Windows and macOS.
Transcription runs **on your own machine** by default — your audio does not leave
it. The name nods to *lect-* (dialect, lecture — speech); the mascot is an
Eclectus parrot.

**[⬇ Download the latest version](https://github.com/FCisco95/lectus-releases/releases/latest)**

## You need to hold ORGANIC or Mycel

Lectus is free for people who hold **$20 of ORGANIC (ORG) or Mycel (MYCEL)**.
Either token is enough. There is no account, no subscription, no card, and no
word limit.

| | ORGANIC | Mycel |
|---|---|---|
| **Ticker** | ORG | MYCEL |
| **Mint** | `DuXugm4oTXrGDopgxgudyhboaf6uUg1GVbJ6jk6qbonk` | `HudkzEWpcUnTYFZMMcbNdwk1S5Am26J2SyEh4NfFworg` |
| **You need** | **$20 worth** of either, held in a wallet you control | |
| **Wallets** | Phantom, Solflare, Backpack | |

You link a wallet **once**, by signing a message. That signature is free, it is
not a transaction, and it **cannot move SOL, tokens, or approve anything** — it
only proves the wallet is yours. Lectus then reads that wallet's ORGANIC and
Mycel balances directly from the Solana chain.

The floor is in **dollars, not tokens**, so the number of ORG or MYCEL needed
follows the live price. Nothing is ever sent anywhere: the balance check is a
public read-only query, and the only thing stored is your wallet's public address.

**If you sell:** dictation keeps working for **7 more days**, with a banner. Top
back up inside that window and nothing is interrupted. Lectus never cuts off a
dictation in progress, and an internet outage cannot lock you out — the 7 days
are counted from the last time your wallet was actually *seen* above the floor,
so a check that never got an answer costs you nothing.

## Install

1. Open the [**latest release**](https://github.com/FCisco95/lectus-releases/releases/latest)
   and download, under **Assets**:
   - **Windows** — `Lectus_x.y.z_x64-setup.exe`
   - **macOS (Apple silicon)** — `Lectus_aarch64.app.tar.gz`; double-click it to
     unpack, then drag `Lectus.app` into **Applications**
2. Open it. The first time, your computer will warn you, because Lectus is not
   yet signed by Microsoft or Apple:
   - **Windows** — "Windows protected your PC": click **More info**, then
     **Run anyway**.
   - **macOS** — if it says Lectus "is damaged" or "cannot be verified", open
     **Terminal**, paste the line below, press Enter, then open Lectus again:
     ```
     xattr -cr /Applications/Lectus.app
     ```
3. Lectus lives in the **system tray** (Windows) / **menu bar** (macOS) and
   starts with your computer, silently.
4. Follow the setup flow:
   - **Link your wallet** — opens your browser, where your wallet extension
     lives, and asks for one signature.
   - **Microphone access** — grant it when your OS asks.
   - **Accessibility** (macOS only) — required to type into other apps.
   - **Pick your dictation key** — the default is **hold Right Ctrl**.

On first run Lectus downloads the multilingual Whisper model (~140 MB) in the
background. Until it lands, a smaller English-only model that ships with the app
covers you.

Updates install themselves: Lectus checks on launch, downloads in the background,
and offers a **Restart now** banner. Nothing happens without your click.

## Using it

**Hold your key, talk, let go.** The text appears where your cursor already was —
any app, any field. That is the whole product.

- **Hold mode** (default) — push-to-talk. Hold Right Ctrl while you speak.
- **Toggle mode** — tap once to start, tap again to stop, for long dictations.
- Click the **floating pill** or the tray icon to open **Home**: your word counts
  for the week and every past dictation, searchable and copyable.

Worth turning on, under Settings:

- **Vocabulary** — names and jargon you want spelled right ("Mycel", not "my cell"),
  plus find/replace rules applied after every transcription.
- **AI cleanup** — punctuation, capitals, and filler removal. Runs through the
  Claude Code CLI on your own subscription, or locally with Gemma.
- **Language** — auto-detect by default; force one (e.g. English inside a code
  editor) globally or per app.
- **Mute while dictating** — silences background playback while your key is held.
- **Cloud backend** — optional Groq `whisper-large-v3-turbo` for more accuracy.
  Off by default; your audio stays local unless you turn it on and add a key.

## Membership questions

**Where do I see my status?** Settings → **Membership**. It shows the linked
wallet, what it holds, what $20 is in ORG today, and a **Check again** button.

**How often is it checked?** Every 12 hours in the background. Your wallet is
never asked to sign again.

**I hold ORG but it says locked.** Hit **Check again**. If the public Solana RPC
is rate-limiting you, point Lectus at your own node by setting the environment
variable `LECTUS_RPC_URL` (for example, a Helius URL).

**What is stored about me?** Your wallet's public address, its last known
balance, and when it was last checked — in `license.json` on your own machine.
Nothing is uploaded. **Unlink** in Settings deletes it.

**Is this DRM?** No. The gate exists so that "Organic holders get Lectus" is
actually true — not to fight anyone. It fails open: inside the 7-day window,
an outage or a slow RPC never blocks you.
