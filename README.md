# tox-windows-issue

Minimal reproducer for [tox issue #2778](https://github.com/tox-dev/tox/issues/2778):

- Jobs succeed with ``tox==3.28.0``: checked with [this commit](https://github.com/stephane-caron/tox-windows-issue/commit/5a73bd326fc9b1ac25b9d863477e54c7f3e21dce) by [this job](https://github.com/stephane-caron/tox-windows-issue/actions/runs/3786963834/jobs/6438334658).
- Jobs fail with ``tox==4.0.18``: checked with [this commit](https://github.com/stephane-caron/tox-windows-issue/commit/b4da8b7ff41a1c49be51b7539f7cc4ee2ea39936) by [this job](https://github.com/stephane-caron/tox-windows-issue/actions/runs/3786982423).

## Follow-up

The issue seems related to a new behavior since tox >= 4.0 where tox started escaping quotes in commands [#2635](https://github.com/tox-dev/tox/issues/2635). There are at least two ways to work around this change if you are experiencing the same issue as in this reproducer:

- Remove all quotes from your commands, *e.g.* escaping spaces and wildcards with backslashes ([example](https://github.com/tox-dev/tox/issues/2635#issuecomment-1367273844)).
- Use previous versions of tox, for instance by adding the following to your ``tox.ini``:

```
[tox]
requires = tox<4
```
