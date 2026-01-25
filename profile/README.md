[![License](https://img.shields.io/github/license/emlang-project/spec)](https://github.com/emlang-project/spec/blob/main/LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/emlang-project/spec)](https://github.com/emlang-project/spec/releases)

Emlang is a YAML-based DSL for describing systems with [Event Modeling](https://eventmodeling.org/) patterns.

## Why Emlang?

Event Modeling is typically done using visual tools like Miro or oNote. These tools are great for collaboration, but diagrams don't fit naturally into a developer's workflow: they can't be versioned, diffed, or reviewed like code.

Emlang bridges that gap:

- **YAML-based** — Version control, diffs, code review workflows
- **Parseable** — Tools can generate diagrams, code, or documentation
- **Complementary** — Works alongside visual tools, not against them

Visual diagrams remain the best way to understand a system. Emlang is a versionable source format that tools can parse to generate those diagrams.

## Quick Reference

| Type      | Short | Long         | Description            |
|-----------|-------|--------------|------------------------|
| Trigger   | `t:`  | `trigger:`   | Initiates an action    |
| Command   | `c:`  | `command:`   | Action/intent          |
| Event     | `e:`  | `event:`     | Past fact              |
| Exception | `x:`  | `exception:` | Failure/error          |
| View      | `v:`  | `view:`      | Projection/Read Model  |

## Example

```yaml
---
flows:
  RegisterUser:
    - t: Customer/RegistrationForm
    - c: RegisterUser
      props:
        email: string
        password: string
    - e: User/UserRegistered
      props:
        userId: uuid
        email: string
    - v: UserProfile

tests:
  DuplicateEmailRejected:
    given:
      - e: User/UserRegistered
        props:
          email: joe@example.com
    when:
      - c: RegisterUser
        props:
          email: joe@example.com
    then:
      - x: EmailAlreadyUsed
```

## Philosophy

Emlang is **minimalist**:

- **Syntax, not semantics** — Emlang defines how to write elements, not what makes a valid model
- **No methodology enforcement** — Event Modeling rules live at https://eventmodeling.org/
- **Tool responsibility** — Validation and code generation are done by separate tools

## Language Specification

The complete specification is available at [emlang-project/spec](https://github.com/emlang-project/spec).

## Learn More

For canonical information about Event Modeling, visit [eventmodeling.org](https://eventmodeling.org/).
