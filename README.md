# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

Blueprints are grouped by type at repository root (for example `automation/`, `script/`).

## Blueprints

### 1) Label state change notifier

- File: `automation/label_state_change.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/automation/label_state_change.yaml`

### Inputs

- **Label**: selected from existing Home Assistant labels
- **State transitions**: list of pairs `from -> to` (newline/semicolon-separated)
  - separators between states supported: `->`, space, `-`, comma
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `entity_id`
- `entity_name`
- `old_state`
- `new_state`
- `transition`
- `change_type` (`connected` / `disconnected`)
