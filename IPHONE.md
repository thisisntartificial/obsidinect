# iPhone: enable Obsidinect in one sitting

Strangers should prefer README path **A** (official directory) or **B** (BRAT) once the GitHub repo is public. This page is path **C**: the three Release files, as screens.

This is the phone walkthrough. Each numbered block is one screen.

## 1. Get the three files onto the vault

**Screen:** Finder, Files, or your Sync folder — not Obsidian yet.

You need a folder named `obsidinect` here:

```text
<your vault>/.obsidian/plugins/obsidinect/
```

Put exactly these files in it (from a build or a release):

- `manifest.json`
- `main.js`
- `styles.css`

If this vault is already in **iCloud Drive** or **Obsidian Sync**, do this on a computer and wait until the phone finishes syncing. You do not install from the App Store.

On iPhone-only setups: use the Files app → the vault folder → `.obsidian` → `plugins` → create `obsidinect` → drop the three files from Files / AirDrop / a files host.

## 2. Open that vault on the phone

**Screen:** Obsidian home / vault picker.

Tap the vault that contains `.obsidian/plugins/obsidinect/`. If you just synced, pull to refresh or wait until the three files appear in Files.

## 3. Turn Restricted mode off

**Screen:** Settings (gear) → Community plugins.

1. Tap **Community plugins**.
2. If you see **Restricted mode is on**, tap **Turn on community plugins** / turn Restricted mode **off**.
3. Confirm if iOS asks.

Obsidinect will not appear while Restricted mode is on.

## 4. Enable Obsidinect

**Screen:** Settings → Community plugins → Installed plugins.

Find **Obsidinect** in the list. Toggle it **on**.

If it is missing: the folder name is wrong, `manifest.json` is missing, or Sync has not finished. The manifest `id` must be `obsidinect` and `isDesktopOnly` must be `false`.

## 5. Paste an API key

**Screen:** Settings → Obsidinect.

1. Pick a provider (Claude is the default).
2. Paste the API key. It is stored in plugin data, not in a note.
3. Leave the model blank to keep the default, or type a model name.
4. Tap **Test connection**. You want a success toast. Failures never print the key.

## 6. Open the chat

**Screen:** A note, then the ribbon / command palette.

- Ribbon: open the left ribbon (or the mobile menu) and tap the robot **Obsidinect** icon.
- Command palette: pull down or tap the palette, type `Open Obsidinect chat`.

**What you should see:** a chat column with the composer pinned to the bottom, large send / attach buttons, and empty-state copy about `@` mentions. The composer stays above the iOS keyboard.

## 7. Attach a note with @

**Screen:** Obsidinect chat, keyboard open.

1. Tap the composer.
2. Type `@` and a few letters of a note name.
3. Tap a row in the list. A chip appears above the composer.
4. Or tap the `@` button and pick a note from the fuzzy list.

Ask something like: `Summarize the attached note in five bullets.`

## 8. Let it edit the vault

**Screen:** same chat, after a write.

Ask: `Create a note called Phone inbox.md with today's errands.`  
If the file already exists and you did not name it, a confirm sheet asks before overwrite. Apply / cancel are full-width tap targets.

## 9. Inline edit a selection

**Screen:** a markdown note.

1. Select a paragraph (or select nothing to edit the whole note).
2. Open the note’s header **pencil** action, or Command palette → **Inline edit**.
3. Type an instruction (`Make this shorter, keep wikilinks`).
4. Tap **Preview edit**. Check Before / After.
5. Tap **Apply**. The editor (or the vault file) updates.

You can also add **Inline edit** to the iOS editing toolbar: Settings → Toolbar / Mobile toolbar → add the command.

## If something is blank

- No plugin in the list → the three files are not in this vault’s `.obsidian/plugins/obsidinect/`.
- Plugin listed but will not enable → `isDesktopOnly` is not `false`, or `main.js` failed to build.
- Chat errors immediately → Test connection, check the key, and confirm the phone can reach `api.anthropic.com`, `api.openai.com`, or `api.x.ai`.
- Composer hidden behind the keyboard → leave the chat, reopen it, and keep Obsidian updated (1.4.0+).
