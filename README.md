# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

## Blueprints

### 1) Label connectivity state change notifier

- File: `blueprints/automation/openclaw/label_connectivity_state_change.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/blueprints/automation/openclaw/label_connectivity_state_change.yaml`

### Inputs

- **Label name**: entities with this label are monitored
- **State transitions**: list of `from->to` pairs (newline/comma/semicolon separated), e.g.
  - `off->on`
  - `on->off`
  - `disconnected->connected`
  - `connected->disconnected`
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `connection_entity_id`
- `connection_entity_name`
- `connection_old_state`
- `connection_new_state`
- `connection_transition`
- `connection_change_type` (`connected` / `disconnected`)
