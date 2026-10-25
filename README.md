# Artist Site Template

Artist-owned source powered by [artist-site-core](https://github.com/Maxwell-Pierce/artist-site-core).

## Get started

```sh
git clone --recurse-submodules https://github.com/Maxwell-Pierce/artist-site-template.git
cd artist-site-template
python .artist-core/scripts/build.py --site . --output _site
```

Edit `artist.json` for the name, palette, hero copy, caption default and entrance effect. Edit `index.html` for layout/content; use `custom.css` or `custom.js` for artist-specific extensions. Place your own videos and artwork in `assets/`. Generated runtime and icons go into `_site/`, not source.

## Music

No playlists are configured yet. Add public Treblo playlist UUIDs to `catalog-source.json`:

```json
{"playlists": [{"id": "your-public-playlist-uuid"}]}
```

The first playlist is played on entry. Run **Actions → Analyze artist lyrics → Run workflow** to refresh catalogs and process the next budgeted set of tracks. The daily schedule continues the queue. Normal UI pushes only build saved results. No DiscoPrincess music or identity assets are included.

## Publishing

Enable **Settings → Pages → Source → GitHub Actions** once for a new repository. The publishing workflow builds and uploads a preview artifact on every PR, and deploys main after checks pass. The template repository itself validates without publishing. A site created from the template will publish normally after Pages is enabled.

## Shared updates

`.artist-core` pins an exact shared commit. Dependabot proposes daily update PRs; review the build artifact and merge to adopt shared fixes. Revert the submodule revision to roll back. Local updates: `git submodule update --init --recursive`; deliberate upgrade: `git submodule update --remote .artist-core`, then commit that revision. Never edit the submodule as though it were artist-owned source.

For GitHub's **Use this template** button, the owner must enable **Settings → General → Template repository** on `artist-site-template`. The source works with a normal clone even before that flag is enabled.

## Edit your website

This starter enables the shared Artist Studio through `builder.json`. After deploying a core version supporting Studio, visit `/admin/`. Connect with a fine-grained repository token (Contents read/write). Edit homepage copy, entrance, colours, navigation and additional pages, preview immediately, save drafts on a separate branch, then Publish. No backend is needed. Repository access tokens are never committed. See `.artist-core/editor/README.md` for permissions, draft recovery and preview limits. To disable the editor, set `enabled` to false.
