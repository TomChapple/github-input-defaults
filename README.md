# GitHub Input Defaults

This repository contains workflows that focus on identifying how the `inputs` context functions outside of its usual circumstance; specifically if the job is triggered by an event that isn't a `workflow_dispatch`.

## Truthiness of Inputs outside `workflow_dispatch`

Executions of this repository's workflow shows that in events outside of
`workflow_dispatch`, the values inside the `inputs` context are treated as
falsey for any conditions relying on them. It appears as though they are
considered blank. As a result, some actions are skipped if we have a condition
based on these inputs during an event such as `push`.

Of particular note is that `inputs` doesn't appear to like being rendered or
used by itself, often appearing as "Object" rather than a JSON object. In fact,
when using `inputs` in a ternary expression, it is always considered truthy.
This might make it tough to discover if the inputs have been provided or not.
