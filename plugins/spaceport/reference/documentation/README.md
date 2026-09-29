# Spaceport framework documentation

The canonical source is [spaceport-dev/documentation](https://github.com/spaceport-dev/documentation).
Read the [published documentation](https://frontier.spaceport.sh/docs/) or fetch a
local reference below. Documentation is maintained upstream; downloaded pages are
an ignored cache, not a second source to edit.

## Fetch locally

Requires Python 3.9+ and curl. Run from the installed plugin root (the directory containing `.claude-plugin/plugin.json`), not your project root:

```sh
(
  set -e
  docs_fetcher="$(mktemp)"
  trap 'rm -f "$docs_fetcher"' EXIT
  curl --fail --silent --show-error --location \
    https://raw.githubusercontent.com/spaceport-dev/documentation/42bdcfc5747cf60ac83fa55efc869462530921dd/fetch.py \
    --output "$docs_fetcher"
  python3 "$docs_fetcher" \
    --revision 42bdcfc5747cf60ac83fa55efc869462530921dd \
    --destination reference/documentation
)
```

This fetches the reviewed revision, including `_index.md`, `_toc.md`, and API
references. It creates no nested Git repository. The helper records the revision
and file checksums in `.spaceport-docs.json`, preserves this README and `.gitignore`,
and leaves existing docs intact if the download fails. It refuses to overwrite
unmanaged files or locally edited cached documents.

## Updating and contributing

To refresh, select a reviewed full commit SHA from the canonical repository and
replace the SHA in both places in the command. Run the same procedure again.
Read `.spaceport-docs.json` to identify the installed version. An offline cache
continues to work until you choose to update it.

If the cache is missing, agents must fetch it before reading framework APIs.
If networking or permissions prevent fetching, report that limitation and consult
the canonical online docs; do not invent APIs or silently use unrelated docs.
Resolve all `reference/documentation/` paths relative to the installed plugin root. Plugin upgrades may clear this cache; fetch it again when needed.

Submit documentation corrections in the canonical repository. Do not commit
fetched Markdown pages here.
