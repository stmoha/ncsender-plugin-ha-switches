# Releasing HA Switches

Same routine as the owner's other ncSender plugins (G-code Explorer, Rotary CAM).

1. **Change and test.** Edit `config.html` (everything happens there; `index.js` only opens it on
   the Node-based v1 / pro-v1 platforms). Bump `manifest.json`'s `version`, add a `CHANGELOG.md`
   entry and rewrite `latest_release.md`. Build a test ZIP with `python package.py vX.Y.Z-test1`
   and install it in ncSender (Settings → Plugins → Install Plugin, then Ctrl+F5).
2. **Commit** to `main` and push.
3. **Publish.** Open
   `https://github.com/stmoha/ncsender-plugin-ha-switches/releases/new?tag=vX.Y.Z&target=main&title=HA%20Switches%20vX.Y.Z`,
   leave the notes empty and click **Publish release**. (Claude's sessions can't create tags or
   releases; the owner clicks this.) The **Build and Release Plugin** workflow checks the tag
   matches `manifest.json`, attaches `com.cncdocs.ha-switches_vX.Y.Z.zip` and fills the notes in
   from `latest_release.md`. Tick *Set as a pre-release* for a beta: ncSender's stable channel
   only sees the latest full release.
4. **Registry.** ncSender's Plugin Manager lists plugins from
   [siganberg/ncSender.plugins-registry](https://github.com/siganberg/ncSender.plugins-registry)
   `plugins.json`. Updates for installed copies come from this repo's releases (the manifest's
   `repository`), so the registry entry only needs a PR when the name, description, icon or
   minimum versions change, or to bump the listed `version`. See `registry-entry.json`.

## Testing without a machine

`config.html` runs inside ncSender's page. Its only server calls are
`/api/plugins/com.cncdocs.ha-switches/settings` (GET/PUT), `/api/send-command` (fallback route)
and the Home Assistant webhook (POST `text/plain`, `{"action":"states"}` or
`{"entity_id": …, "action": "on|off|toggle"}`). A small aiohttp server that serves `config.html`
inside a mock dialog, stores settings and fakes the webhook is enough to exercise every state.
