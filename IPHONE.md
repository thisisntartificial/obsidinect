# Install Claudius on iPhone

Public repo: https://github.com/thisisntartificial/obsidinect

## BRAT (do this)

Claudius is not in Browse yet.

1. Open the vault on your iPhone.
2. Settings → Community plugins → turn **Restricted mode** off.
3. Browse → install **BRAT** → enable it.
4. Settings → BRAT → **Add beta plugin**.
5. Paste `thisisntartificial/obsidinect`.
6. Enable **Claudius**.
7. Settings → Claudius → pick Claude / ChatGPT / Grok → paste your API key → **Test connection**.
8. Tap the robot **Claudius** icon (ribbon / mobile menu) and chat.

Type `@` to attach a note. Ask it to write or edit notes. Select text and use **Inline edit** for a before/after preview.

## Manual (three files, if you skip BRAT)

Put these Release files in the vault:

```text
<your vault>/.obsidian/plugins/obsidinect/manifest.json
<your vault>/.obsidian/plugins/obsidinect/main.js
<your vault>/.obsidian/plugins/obsidinect/styles.css
```

Download them from https://github.com/thisisntartificial/obsidinect/releases/tag/1.0.0

If the vault is in iCloud or Obsidian Sync, drop the files on a computer and wait. iPhone-only: Files app → vault → `.obsidian` → `plugins` → create `obsidinect` → drop the three files.

Then: open that vault → Restricted mode off → enable **Claudius** → paste an API key.

## If something is blank

- No plugin in the list → BRAT did not add it, or the three files are not in `.obsidian/plugins/obsidinect/`.
- Plugin listed but will not enable → wait for sync, or `isDesktopOnly` is not `false`.
- Chat errors immediately → Test connection, check the key, and confirm the phone can reach the provider.
