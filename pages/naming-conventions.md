# Naming Conventions
Use these, they're good.

## Conventions to use
| Type          | Convetion
| ------------- |-------------
| Variable      | `SNAKE_CASE_ALL_CAPS`
| Tag           | `PascalCase`
| Trigger       | `camelCase`

## Why?
Tag Manager's Search function is pretty good. Searching for `jquery` when you have a tag, variable and trigger all defined with jquery in the name could be difficult. With a decent naming convetion you'll know which is which.

## Warning on Namespaces
It's common to see namespaces used in GTM, don't do that. `my_project_some_variable` suggests that a variable has limited scope, it usually doesn't so there's no point. It also makes searching for stuff a bit of a nightmare, the results list will be `my_proj...` which is no good.