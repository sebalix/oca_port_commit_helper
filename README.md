OCA Port Commit Helper
======================

Tool to ease the port of commits (forward port or backport) from one branch to another on OCA.

How to use it:

    $ ./oca_port_commit_helper {REPO_PATH} {MODULE} {FROM_BRANCH} {TO_BRANCH}

Example:

```sh
$ ./oca_port_commit_helper ~/oca/wms/shopfloor OCA/13.0 OCA/14.0
85 commits to port from OCA/13.0 to OCA/14.0

9c174436381da48a761a3fc18fb8c50288fb32e0 [FIX] sf, loc. content transfer: put lines in separate transfer (fix)
560906c77bedad7b26828a88e2df92ed9b8d9047 [FIX] sf, loc. content transfer: put lines in separate transfer (test)
17773852ac05e1167a5023541e8c0d73dda934e1 shopfloor: zone_picking add pick+pack option
0244c05be7bd5b57cd71d813125771350a27557f shopfloor, checkout: get right carrier
[...]
```

As branches are not related to each other (no common history), the following commit attributes are used to uniquely identify a commit among two branches:

- `author name`
- `author email`
- `authored date`
- `message`

These attribute values should not change over time even if the commit has been cherry-picked or rebased.
