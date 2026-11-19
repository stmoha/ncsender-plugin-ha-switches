# Changelog

Versions before 0.1.9 were developed inside [ha-ncsender](https://github.com/stmoha/ha-ncsender)
(`ncsender-plugin/`); this repo keeps their history.

## 0.1.9 — first release from this repo
- **Edit HA Switches settings** bar (was "Edit switches") with a chevron and a "Click to open /
  Click to close" hint, plus a *Close settings* button next to Save.
- The switch list is coloured with ncSender's own editor colours (dark and light themes): names,
  entity IDs, `hold` / `slow`, `#` notes, and anything that isn't an entity ID underlined in red,
  with a key below.
- `manifest.json` points at this repo, so ncSender offers updates from its releases.

## 0.1.8
- `#` notes: start a line with `#` to comment it out, or put a note after an entry. The list is
  saved as typed, so notes survive Save.

## 0.1.7
- Optional `slow` flag (`Name, entity_id, slow`, combinable with `hold`): the toggle keeps pulsing
  for up to 15 minutes instead of 10 s, for devices such as a compressor that finishes its cycle
  before powering off.

## 0.1.6
- After a tap the toggle moves at once and pulses "Switching on…" until Home Assistant reports the
  new state, instead of flicking back while a device such as a Shelly catches up.

## 0.1.5
- With the webhook set, each device is one toggle showing its live state; unavailable or not-allowed
  devices show red and can't be pressed. Without a webhook: On/Off buttons.

## 0.1.4
- Optional hold-to-press per switch (`Name, entity_id, hold`), like ncSender's own *Hold* outputs.

## 0.1.3
- *Keyboard shortcuts…* also types "HA Switches" into the Controls search.

## 0.1.2
- Direct route: *Home Assistant webhook URL* setting (integration v0.5.0b2+), live on/off state,
  *Open Home Assistant* link, *Keyboard shortcuts…* button, official Home Assistant icon.

## 0.1.1
- Pressing inside the dialog and releasing outside no longer closes it; unsaved edits block
  backdrop clicks and are restored when the dialog reopens; more padding.

## 0.1.0
- Prototype: Tools-menu dialog whose buttons send `(HA <entity_id> ON|OFF)` comment lines.
