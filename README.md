# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

Blueprints are grouped by type at repository root (for example `automation/`, `script/`).

## Blueprints

### 1) Label state change notifier

- File: `automation/label_state_change.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/automation/label_state_change.yaml`

### Inputs

- **Label**: selected from existing Home Assistant labels (used directly in trigger, not post-filter)
- **Transition rules**: list of lines `<from><sep><to> : <name>` (newline/semicolon-separated)
  - separators between states supported: `->`, space, `-`, comma
  - wildcard source: empty or `*` (examples: `->off`, `*->on`, `-unavailable`)
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `entity_id`
- `entity_name`
- `old_state`
- `new_state`
- `transition`
- `transition_name`

### Notes

- Automation now triggers only for entities from the selected label.
- If label membership changes, reload automations (or restart HA) to refresh trigger entity list.
