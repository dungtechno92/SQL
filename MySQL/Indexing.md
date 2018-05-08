1. Types of Indexes:
  1.1. B-Tree indexes:
    - Kinds of queries: 
      + Match the full value.
      + Match a leftmost prefix.
      + Match a column prefix.
      + Match a range of values.
      + Match one part exactly and match a range on another part.
      + Index-only queries.
    - Limitations: 
      + Not useful if the lookup does not start from the leftmost side of the indexed.
      + Can’t skip columns in the index(when use index for multi columns).
      + The storage engine can’t optimize accesses with any columns to the right of the
      first range condition.
  1.2. Hash indexes:
    - Limitations:
      + Can't use the values in the index to avoid reading the rows.
      + Can't use hash indexes for sorting.
      + Hash indexes don’t support partial key matching.
      + Hash indexes support only equality comparisons.
      + Some index maintenace operations can be slow if there are many hash collisions.
    - Adaptive hash indexes( TODO).
2. Benefits of indexes:
  - Indexes reduce the amount of data the server has to examine.
  - Indexes help the server avoid sorting and temporary tables.
  - Indexes turn random I/O into sequential I/O.
  * Note: At a high level, keep in mind that indexes are most effective when they help 
  the storage engine find rows without adding more work than they avoid.
3. Indexing Strategies for High Performance:
  3.1. Isolating the Column:
  3.2. Prefix Indexes and Index Selectivity:
  3.3. Multicolumns Indexes:
        - When we use intersects indexes(usually for AND conditions). It usually means we need 
        a single index with all relevant columns, not multiple indexes that have to conbined.
        - When we use union indexes(usually for OR conditions), some time algorithm' buffering
        , sorting and megering operation may uses a lot of CPU, memory. Consider about ignore index.
        - Recall that the optimizer doesn’t account for this cost—it optimizes just the number
        of random page reads.

