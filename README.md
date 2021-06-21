OCA Port Commit Helper
======================

Tool to ease the port of commits (forward port or backport) from one branch to another on OCA.

How to use it
=============

    $ export GITHUB_TOKEN={TOKEN}
    $ ./oca_port_commit_helper {REPO_PATH} {REPO_NAME} {MODULE} {FROM_BRANCH} {TO_BRANCH}

Example:

```sh
$ export GITHUB_TOKEN=zdisqljdlkqjflsufoxwjkljflkdsqjfslkiomza
$ ./oca_port_commit_helper ~/oca/wms wms shopfloor OCA/13.0 OCA/14.0
85 commits to port from OCA/13.0 to OCA/14.0

2021-01-13 09:10:57: https://github.com/OCA/wms/pull/104:
	fec8bc94bfbf6a25fdf7f8842967c4f16e1ea870 [FIX] shopfloor: cluster picking, remove unavailable picking from validated batch

2021-01-13 11:16:22: https://github.com/OCA/wms/pull/84:
	9d6c04e67b9932b9f14fea226dbec719d88c3650 [FIX] shopfloor, checkout: ability to recover/restart

2021-01-13 13:48:43: https://github.com/OCA/wms/pull/99:
	8c5a939fa5ba62ef85352494ef7fc9cd84fd2773 shopfloor: improve service header validation
	e963487ddf66ac6bb3d630c3edba73b81091127b shopfloor: refactor zone_picking.scan_source
	b0c90f60ead953d44e6c11fe341a954c268a73f8 shopfloor: message fix multiple calls to gettext
	e6dab743fc91af76e0a514dd3349163eeecfe03a shopfloor: zone_picking.scan_source fix scan location
[...]
```

A authorization token is required to bypass the limit or requests with GitHub API.

How it works
============

As branches are not related to each other (no common history), the following commit attributes are used to uniquely identify a commit among two branches:

- `author name`
- `author email`
- `authored date`
- `message`

These attribute values should not change over time even if the commit has been cherry-picked or rebased.

Some commits are ignored on purpose like the ones created by OCA bots, the update of translations and merge commits.
