# ha-blueprints

Home Assistant blueprints by [@avchaykin](https://github.com/avchaykin).

Blueprints are grouped by type at repository root (for example `automation/`, `script/`).

## Blueprints

### Motion activated light with condition

- File: `automation/motion_activated_light_with_condition.yaml`
- Import URL:

`https://raw.githubusercontent.com/avchaykin/ha-blueprints/main/automation/motion_activated_light_with_condition.yaml`

### Inputs

- **Motion sensor**: binary motion/occupancy sensor that triggers the automation
- **Light sources**: target containing lights/switches to turn on/off
- **Duration**: time in seconds to keep sources on
- **Condition**: Home Assistant condition that must be true before turning sources on

### Behavior

- On motion (`on`) checks the configured condition.
- If condition is true, turns on selected sources.
- Waits for the configured duration.
- If the motion/occupancy sensor is still active (`on` / UI `yes`), keeps the sources on.
- Turns sources off only after the sensor becomes inactive (`off` / UI `no`).
- `mode: restart` means repeated motion restarts the timer.

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
- **Ignore unknown/unavailable transitions**: toggle to drop these changes before rule matching
- **Actions**: your custom actions (can use blueprint variables below)

### Variables available in actions

- `entity_id`
- `entity_name`
- `entity_area`
- `entity_area_name`
- `old_state`
- `new_state`
- `transition`
- `transition_name`
- `entity_domain`

### Notes

- Label membership changes are applied immediately (no automation reload required).
- Internally this uses `state_changed` + dynamic filters, so it stays flexible when labels are edited.
- Debounce waits N seconds and runs actions only if entity is still in the same `new_state`.
