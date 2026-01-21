Emlang is a text-based DSL for describing systems with [Event Modeling](https://eventmodeling.org/) patterns.

## Why Emlang?

Event Modeling is typically done using visual tools like Miro or oNote. These tools are great for collaboration, but diagrams don't fit naturally into a developer's workflow — they can't be versioned, diffed, or reviewed like code.

Emlang bridges that gap:

- **Text-based** — Version control, diffs, code review workflows
- **Parseable** — Tools can generate diagrams, code, or documentation
- **Complementary** — Works alongside visual tools, not against them

Visual diagrams remain the best way to understand a system. Emlang is a versionable source format that tools can parse to generate those diagrams.

## Example

```emlang
; This is an example of an Emlang document

/UserRegistration/
  %Customer:RegistrationForm%
  [RegisterUser]
    email
    password
  <User:UserRegistered>
    userId
    email
  {UserProfile}

---  

?EmailAddressMustBeUnique?
  <UserRegistered>
    email: joe@example.com
  [RegisterUser]
    email: joe@example.com
  !EmailAddressAlreadyUsed!
```

## Philosophy

Emlang is **minimalist**:

- **Syntax, not semantics** — Emlang defines how to write elements, not what makes a valid model
- **No methodology enforcement** — Event Modeling rules live at https://eventmodeling.org/
- **Tool responsibility** — Validation and code generation are done by separate tools

## Status

Emlang is a new project and a work in progress. However, the need for a text-based Event Modeling format is not new — it emerged from years of practice with visual modeling tools.

## Language Specification

[![Latest Release](https://img.shields.io/github/v/release/emlang-project/spec)](https://github.com/emlang-project/spec/releases)

The Emlang language specification is available at [emlang-project/spec](https://github.com/emlang-project/spec).

## Learn More

For canonical information about Event Modeling, visit [eventmodeling.org](https://eventmodeling.org/).
