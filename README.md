# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

All blueprint files are stored in the repository root.

## Blueprints

### 1) Label state change notifier

- File: `label_state_change.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/label_state_change.yaml`

### Inputs

- **Label name**: entities with this label are monitored
- **State transitions**: list of `from->to` pairs (newline/comma/semicolon separated), e.g.
  - `off->on`
  - `on->off`
  - `disconnected->connected`
  - `connected->disconnected`
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `entity_id`
- `entity_name`
- `old_state`
- `new_state`
- `transition`
- `change_type` (`connected` / `disconnected`)
