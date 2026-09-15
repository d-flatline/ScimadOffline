# ScimadOffline

A complete offline copy of the Sciencemadness "Whisper" discussion board,
with a terminal browser for reading it. Captured 2026-09-15.

The archive is attached to the [latest release](../../releases/latest).

## Archive contents

| file | |
|---|---|
| `scimad.sqlite3` | 20 forums, 38,589 topics, 498,607 posts, 10,482 users (1,442 MB) |
| `scimad_tui.py` | terminal browser |
| `README.txt` | usage, schema notes, direct-SQL examples |

The FTS5 full-text search index lives **inside** `scimad.sqlite3` (tables
`posts_fts*`). There are no separate index files and nothing to rebuild after
extraction.

```
scimad-offline-2026-09-15.tar.xz   253,685,428 bytes
sha256  02f5a19243f5087ff3d3042414da6c973e01606ba4e69ddf06e0560b584b6991
```

## Use

```bash
tar -xf scimad-offline-2026-09-15.tar.xz
cd scimad-offline
python3 -m pip install textual
python3 scimad_tui.py --db scimad.sqlite3
```

`/` search · `t` topic-title vs post-text search · `enter` open · `n`/`p` page
· `esc` back · `q` quit

It is also an ordinary SQLite database:

```bash
sqlite3 scimad.sqlite3 "SELECT title FROM threads ORDER BY post_count DESC LIMIT 5;"
```

## Notes

Text only — attached files were not downloaded, though the `attachments` table
records that a post had one. Built with
[scimad-spider](https://github.com/d-flatline/scimad-spider).

Posts are the copyright of their individual authors.
