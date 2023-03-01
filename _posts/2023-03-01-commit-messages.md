---
layout: post
title:  "Commit message convention"
author: vitor
categories: [ team, bahamut, github, agreement ]
image: assets/images/commit-message-convention.png
description: "A document describing our commit message convention that our tech team used across projects."
featured: false
hidden: false
---
Our tech team agreement on commit message conventions.

# Introduction

Good commit messages are important for maintaining projects and is the best way to
communicate context about changes to other developers. Besides that, it will help us
keep track of all commits and know exactly what changes were made in each commit.

This proposal aims to add more semantic meaning and create an understandable, readable,
useful, and structured git commit history.

In the near future will help us with:

- Automatic changelog generation
- Determine semantic version bump
- Releases notes for the project

In this proposal we will follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).
It is a specification that provides easy rules for creating an explicit commit history which makes it easy
for humans and machines to understand.

# Commit Message

```
<type>[(optional scope)]: <description>

[optional body]

[optional footer(s)]
```

## Type

- Communicate the intent of changes
- Any case may be used, the important is to be consistent
    - Since one of the goals is a readable git history maybe we might use the capitalized one
    - **Lowercase**
- Most general **&lt;type&gt;** values:
    - `feat:` A **new feature**
        - Eg:
            - `feat(state): add new state properties`
    - `fix:` A **bug fix**
        - Eg:

        ```
        fix(timeDimension): disable previous and next arrows (Monthly)

        Disable previous and next month arrows when there is no more month composites
        ```

    - `refactor:` Changes related with **codebase modifying**, which **neither fixes a bug** nor
      **adds a feature** (Eg: renaming variable, improving functionalities, removing redundant code, simplifying the code, etc)
        - Eg:
            - `refactor(mini-maps): update rendering behavior`
            - `refactor(menu-selection): area selection behavior upgraded`
- Other **&lt;type&gt;** values:
    - `chore:` Changes related to the **build system** (involving scripts, configurations or tools),
      **package dependencies** (eg: change to .gitignore file or .prettierrc file).
    - In **special cases**, could be used for **codebase styling** (Eg: indentations, quotes, trailing commas,
      missing semi colons, white-space, formatting, etc)
        - Eg:
            - `chore(npm): update axios to 0.17.1`
            - `chore(docs-infra): upgrade webpack to 3.2.4`
            - `chore(report): fix indentation in report component`
    - `ci:`  Changes related to the **continuous integration** and **deployment** system - involving scripts, configurations or tools
        - Eg:
            - `ci(aws): unset default aws profile for CI deployment`
    - `docs:` Changes related to the **project documentation**
        - Eg:
            - `docs(change-log): update change log to RC.3`
    - `test:` Adding missing tests or correcting existing tests
        - Eg:
            - `test(tsl-map): add test for tsl-map component`

## Optional scope

- Provide additional contextual information
- Should be nouns and surrounded by parentheses
- Should always be lowercase
- Case style:
    - **kebab-case**
- By adding an exclamation `!` **** mark before the colon `:` is possible understand if the commit has any breaking changes
    - Eg: `refactor(vue)!: drop support for vue 2`

## Description

- Short message that describes what the commit does
- It should be written in the imperative, present tense (&quot;_change&quot;_ not &quot;_changed&quot;_ nor &quot;_changes&quot;_)
- Don&#39;t capitalize the first letter

The first commit line **can&#39;t** be longer than **70 characters**.

Eg: in the image below you can see:

**1 -** The more info button is due to added _optional body_.

**2 &amp; 3 -** The **maximum character limit** (**70**) was exceeded and the sentence was cut off.

![examples](/assets/images/commit-message-example.png)

## Optional body

- Used to explain what changes were made and why was made
- Not all commits are complex enough to need a body

Each body line should be wrapped between **80 characters** maximum.

## Optional footer

- Should contain any information about **Breaking Changes**
    - **Breaking Changes** should start with the word `BREAKING CHANGE:` with a space. The rest of the commit message
      is then used for this.
    - All **Breaking Changes** have to be mentioned in footer with the description of the change and justification notes.
- Place to reference GitHub issues that this commit **Closes,** mainly used when using an issue tracker to reference the issue ID
- Can also be used for other metadata options

---

Any line of the commit message cannot be longer than **80 characters**! This allows the message to be **easier**  **to read** on GitHub.

---

## Samples

### Simple commit messages

```
feat(config): allow provided config object to extend other configs
```

```
docs(change-log): update changelog to beta.5
```

```
fix(router): update api endpoint
```

### Commit message with body

```
fix(release): need to depend on latest rxjs and zone.js

The version in our package.json gets copied to the one we publish, and users
need the latest of these.
```

```
fix(middleware): ensure Range headers adhere more closely to RFC 2616

Add one new dependency, use `range-parser` (Express dependency) to compute
range. It is more well-tested in the wild.

Closes #2310
```

### Commit message with Breaking Change

```
refactor!: drop support for Node 6
```

```
refactor(runtime)!: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.
```

It is possible to find other examples in: [**Conventional commit samples**](https://www.conventionalcommits.org/en/v1.0.0/#examples).
