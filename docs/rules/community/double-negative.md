# double-negative

> **Note:** This rule is currently only available as part of the
> ✨ _Regal Festive Promotion_ ✨. If you'd like to take part,
> and use this rule, please give [Regal](https://github.com/styraInc/regal)
> a quick star on GitHub and join `#community` channel in the
> [Styra Community Slack](https://communityinviter.com/apps/styracommunity/signup)
> for more details.

**Summary**: Avoid double negatives

**Category**: Community

**Avoid**
```rego
package negative

import future.keywords.if

fine if not not_fine

with_friends if not without_friends

not_fine := input.fine != true

without_friends if count(input.friends) == 0
```

**Prefer**
```rego
package negative

import future.keywords.if

fine if input.fine == true

with_friends if count(input.friends) > 0
```

## Rationale

While rules using double negatives — like `not no_funds` — occasionally make sense, it is often worth considering
whether the rule could be rewritten without the negative. For example, `not no_funds` could be rewritten as `funds` or
`has_funds`, or `funds_available`.

Access control policy often includes rules using some form of double negatives, like `allow if not deny`. That's
considered OK, and the `double-negative` rule is limited to check for a limited list of words:

* `not cannot_`
* `not no_`
* `not non_`
* `not not_`,

## Configuration Options

This linter rule provides the following configuration options:

```yaml
rules:
  community:
    double-negative:
      # one of "error", "warning", "ignore"
      level: error
```

## Community

If you think you've found a problem with this rule or its documentation, would like to suggest improvements, new rules,
or just talk about Regal in general, please join us in the `#regal` channel in the Styra Community
[Slack](https://communityinviter.com/apps/styracommunity/signup)!
