# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

Blueprints are grouped by type at repository root (for example `automation/`, `script/`).

## Blueprints

### 1) Label state change notifier

- File: `automation/label_state_change.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/automation/label_state_change.yaml`

### Inputs

- **Label**: selected from existing Home Assistant labels (checked dynamically)
- **Transition rules**: list of lines `<from><sep><to> : <name>` (newline/semicolon-separated)
  - separators between states supported: `->`, space, `-`, comma
  - wildcard source: empty or `*` (examples: `->off`, `*->on`, `-unavailable`)
- **Entity domains filter (optional)**: `binary_sensor,sensor` by default, empty = all domains
- **Debounce seconds**: optional anti-flap hold time before actions
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `entity_id`
- `entity_name`
- `old_state`
- `new_state`
- `transition`
- `transition_name`
- `entity_domain`

### Notes

- Label membership changes are applied immediately (no automation reload required).
- Internally this uses `state_changed` + dynamic filters, so it stays flexible when labels are edited.
- Debounce waits N seconds and runs actions only if entity is still in the same `new_state`.
