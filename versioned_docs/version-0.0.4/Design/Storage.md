---
title: Storage
weight: 1
---

The research conducted with LingoDB does not focus on storage aspects of database systems.
Thus, LingoDB does not come with an optimized storage backend and currently does not provide transactional semantics.

## In-Memory Format: Apache Arrow

The Apache Arrow columnar layout is used for the in-memory representation of tabular data.
Thus, LingoDB can exchange data with existing libraries and frameworks without any overhead and can directly query
Apache Arrow tables.

## Persistent Storage

For many practical purposes, persistent storage is required.
We chose a pragmatic approach:

1. Each database is represented by multiple files placed in one *database directory*
2. The main database file is called `db.lingodb` and contains the database catalog and metadata in a binary format
3. At the moment, further files are used to store the table data (e.g., in Apache Arrow format)

Given the database directory, LingoDB automatically loads the database catalog and metadata from the `db.lingodb` file.
