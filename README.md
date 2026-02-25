# Filters

This repository contains generated filter lists and a manifest for blocked-domain datasets.
It is the public output of the filters-downloader pipeline and is not intended to be edited manually.

## Repository layout

- hosts/ : Generated filter lists grouped by provider and category.
  - adguard/
  - easylist/
  - others/
  - parental/
- icons/ : Provider and language icons referenced by the manifest.
- manifest.json : Index of all generated filters, metadata, and output paths.

## Manifest format

The manifest is a JSON document with a top-level filters array. Each entry includes:

- id, provider, category, collection_id
- output_file (relative path under hosts/)
- source_url
- domains_count, file_size_bytes
- sha256
- updated_at, version
- input_format, languages

## Update flow

This repository is updated by the filters-downloader GitHub Actions workflow:

- The downloader generates data/filters and data/manifest.json in the private repo.
- The workflow syncs data/filters to hosts/ and copies icons/.
- The public manifest is copied to manifest.json.

If you need to change sources or parsing behavior, update the filters-downloader repo instead.

## Contributing

Direct edits in this repository will be overwritten by the next sync. Please submit changes to
filters-downloader/config/filters.json or the downloader scripts.

