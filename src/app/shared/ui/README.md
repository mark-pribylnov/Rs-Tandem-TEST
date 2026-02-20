# TNDM UI Kit

A library of reusable, high-performance UI components for the TNDM project. Built with **Angular Signals** and **OnPush** strategy.

---

## Table of Contents

- [General Principles](#general-principles)
- [Form Components](#form-components)
  - [TndmInputComponent](#tndminputcomponent)
  - [TndmCheckboxComponent](#tndmcheckboxcomponent)
- [Action Components](#action-components)
  - [TndmButtonComponent](#tndmbuttoncomponent)
- [Shared Types](#shared-types)

---

## 🏗 General Principles

### Reactive Forms (CVA)

All form components implement `ControlValueAccessor`. This allows seamless integration with Angular Reactive Forms:

```html
<tndm-input-component formControlName="userName" />
```

### Validation Priority

Error messages are resolved in the following order:

1. **Custom Message** — from `errorMessages` input
2. **Default Message** — fallback from `DEFAULT_ERROR_MESSAGES` constant

---

## Form Components

### TndmInputComponent

A versatile text field supporting various HTML5 input types and validation states.

#### 📸 Visual States

| Default                                    | With Icon                                     | Focus/Hover                                    | Error State                                   | Disabled                                    |
| ------------------------------------------ | --------------------------------------------- | ---------------------------------------------- | --------------------------------------------- | ------------------------------------------- |
| ![Default](./docs/input/input-default.png) | ![WithIcon](./docs/input/input-with-icon.png) | ![Default](./docs/input/input-focus-hover.png) | ![Default](./docs/input/input-with-error.png) | ![Default](./docs/input/input-disabled.png) |

#### API (Inputs)

| Property      | Type                   | Required | Default | Description                                   |
| ------------- | ---------------------- | -------- | ------- | --------------------------------------------- |
| id            | string                 | ✅       | —       | Unique identifier for label/input binding     |
| name          | string                 | ✅       | —       | Field name used for generating error messages |
| label         | string                 | ❌       | null    | Text label displayed above the input          |
| type          | InputType              | ❌       | text    | HTML input type (email, password, etc.)       |
| placeholder   | string                 | ❌       | null    | Ghost text displayed inside the field         |
| icon          | IconType               | ❌       | null    | Icon name from the internal library           |
| errorMessages | Record<string, string> | ❌       | {}      | Custom error message overrides                |

#### Usage

```html
<tndm-input-component
  formControlName="email"
  id="user-email"
  name="email"
  type="email"
  icon="email"
  [errorMessages]="{ required: 'email is mandatory' }">
</tndm-input-component>
```

### TndmCheckboxComponent

**Status:** 🛠 Planed
Custom checkbox implementation with CVA support.

---

## Action Components

### TndmButtonComponent

**Status:** Done
Standardized button system supporting multiple variants (primary, secondary, icon).

---

## Shared Types

- **InputType:** `email | password | search | tel | text | url`
- **IconType:** `keyof typeof ICONS` (specific keys from the internal icon library)
