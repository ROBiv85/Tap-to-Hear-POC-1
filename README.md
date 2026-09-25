# Tap to Hear — Web Proof of Concept

This is the fastest version for tonight.

What it proves:

1. Record audio on the iPhone in Safari.
2. Save that recording locally in Safari using IndexedDB.
3. Generate a unique memory URL.
4. Copy that URL into an NFC-writing app such as NFC Tools.
5. Tap the physical NFC tag.
6. Safari opens the memory URL.
7. The saved recording is available for playback.

## Important limitation

This POC stores the audio only in Safari on the iPhone where you created it.

That means the programmed NFC tag will work on THAT iPhone/browser profile, but another customer's phone cannot retrieve the recording yet.

That is intentional. The next version replaces local IndexedDB storage with Supabase Storage/database so any authorized device can retrieve the memory.

## Fast launch option: GitHub Pages

You need HTTPS for reliable microphone access on iPhone.

1. Create a new GitHub repository, for example `tap-to-hear-web-poc`.
2. Upload:
   - `index.html`
   - `manifest.webmanifest`
3. In GitHub open:
   Settings → Pages
4. Under "Build and deployment":
   - Source: Deploy from a branch
   - Branch: `main`
   - Folder: `/ (root)`
5. Save.
6. Wait for GitHub to show the HTTPS Pages URL.
7. Open that URL in Safari on your iPhone.
8. Allow microphone permission.
9. Record → stop → preview → save.
10. Copy the generated memory URL.

## Write the NFC tag

Using NFC Tools on the iPhone:

1. Open NFC Tools.
2. Tap Write.
3. Add a record.
4. Choose URL / URI.
5. Paste the generated memory URL.
6. Tap Write.
7. Hold the top of the iPhone near the NTAG215.
8. Do NOT lock the tag.

## Test

1. Close NFC Tools.
2. Tap the programmed NTAG215 near the top of the iPhone.
3. Open the detected URL.
4. Safari should load the Tap to Hear memory screen.
5. Tap Play.

## Why playback may require one tap

iOS/Safari commonly prevents audio autoplay unless the user interacts with the page first. That is normal browser behavior and not an NFC problem.
