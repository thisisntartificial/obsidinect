# Share Obsidinect with strangers

Origin is the working repo. The official Obsidian directory only accepts a **public GitHub** repository plus a GitHub Release. Do **not** invent an owner or repo slug here. Fill the blanks when the GitHub repo exists.

Product name: **Obsidinect**  
Plugin id: **`obsidinect`** (must not contain the substring `obsidian`)  
Install folder: `.obsidian/plugins/obsidinect/`

## Before anyone else can install

- [ ] Create a **public** GitHub repository and push this project (keep `id` as `obsidinect`).
- [ ] Replace `AUTHOR_HANDLE` in `manifest.json` with Robert’s real GitHub username. The community browser shows this as the author. Do this **before** the directory PR.
- [ ] Leave `fundingUrl` omitted unless you have a real funding link.
- [ ] Confirm `isDesktopOnly` is `false` (required for iPhone).
- [ ] Confirm the repo has **no API keys**. Every user pastes their own key in Settings.
- [ ] Write the public GitHub URL here (do not guess): `https://github.com/________________/________________`
- [ ] Write the `repo` field for the directory (form `owner/name`): `________________/________________`

## Publish a version strangers can download

1. Bump the version in `package.json` / `manifest.json` (or `npm version`).
2. `versions.json` must map that version to `minAppVersion` (`1.4.0` today). `npm version` and the Release workflow both update this file.
3. Push the commit, then push a tag named after the version:

```bash
git tag 1.0.0
git push origin 1.0.0
```

4. GitHub Actions (`.github/workflows/release.yml`) builds the plugin and **publishes** a Release whose **title is the version** (for example `1.0.0`) and attaches **exactly**:
   - `main.js`
   - `manifest.json`
   - `styles.css`

That is what BRAT and the official directory download. Do not attach source maps, zips-as-the-only-asset, or `node_modules`.

Optional local zip for AirDrop: `npm run package` → `obsidinect-<version>.zip`.

## Tell other people, in this order

Copy the [README install section](README.md#install-for-other-people):

1. **A.** Official directory, once listed: Settings → Community plugins → Browse → search **Obsidinect** → Install. Works on iPhone after Restricted mode is off.
2. **B.** BRAT, the day the GitHub repo is public: install BRAT → Add beta plugin → paste the GitHub repo URL.
3. **C.** Manual: download the three Release files into `.obsidian/plugins/obsidinect/`.

## Copy-paste PR for the official directory

Open a PR against [obsidianmd/obsidian-releases](https://github.com/obsidianmd/obsidian-releases) that appends **one object** to the end of `community-plugins.json`.

The directory validator only allows these keys: `repo`, `id`, `name`, `author`, `description`. `isDesktopOnly` belongs in `manifest.json` (must stay `false`); mention it in the PR body, not in the JSON.

Replace the `________________` blanks. Do not invent an owner.

### `community-plugins.json` entry

```json
{
    "id": "obsidinect",
    "name": "Obsidinect",
    "author": "AUTHOR_HANDLE",
    "description": "Chat with Claude, ChatGPT, or Grok in your vault on iPhone and desktop. The agent can read, write, and search notes. No desktop CLI.",
    "repo": "GITHUB_USER/REPO"
}
```

### PR title

```text
Add plugin: Obsidinect
```

### PR body

```text
Adding Obsidinect to community-plugins.json.

- repo: GITHUB_USER/REPO
- id: obsidinect
- name: Obsidinect
- author: AUTHOR_HANDLE
- description: Chat with Claude, ChatGPT, or Grok in your vault on iPhone and desktop. The agent can read, write, and search notes. No desktop CLI.
- isDesktopOnly: false (in manifest.json — required so the plugin loads on iPhone)

Checklist
- [ ] Public GitHub repo is live
- [ ] AUTHOR_HANDLE in manifest.json is Robert’s real GitHub username
- [ ] Latest GitHub Release title matches manifest version (e.g. 1.0.0)
- [ ] Release attaches exactly main.js, manifest.json, styles.css
- [ ] versions.json on the default branch lists that version
- [ ] I am the owner (or a public member of the owning org)
- [ ] Plugin id does not contain the substring "obsidian"
- [ ] No API keys in the repository
- [ ] Description is an action sentence, under 250 characters, ends with a period, no emoji

I read https://github.com/obsidianmd/obsidian-releases and added the entry at the end of community-plugins.json.
```

After the directory lists it, path A in the README starts working on desktop and iPhone.
