## Types of Indexes:
### B-Tree indexes:
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
### Hash indexes:
    - Limitations:
      + Can't use the values in the index to avoid reading the rows.
      + Can't use hash indexes for sorting.
      + Hash indexes don’t support partial key matching.
      + Hash indexes support only equality comparisons.
      + Some index maintenace operations can be slow if there are many hash collisions.
    - Adaptive hash indexes( TODO).
## Benefits of indexes:
  - Indexes reduce the amount of data the server has to examine.
  - Indexes help the server avoid sorting and temporary tables.
  - Indexes turn random I/O into sequential I/O.
  * Note: At a high level, keep in mind that indexes are most effective when they help 
  the storage engine find rows without adding more work than they avoid.
## Indexing Strategies for High Performance:
### Isolating the Column:
### Prefix Indexes and Index Selectivity:
### Multicolumns Indexes:
    - When we use intersects indexes(usually for AND conditions). It usually means we need 
    a single index with all relevant columns, not multiple indexes that have to conbined.
    - When we use union indexes(usually for OR conditions), some time algorithm' buffering
    , sorting and megering operation may uses a lot of CPU, memory. Consider about ignore index.
    - Recall that the optimizer doesn’t account for this cost—it optimizes just the number
    of random page reads.
### Clustered indexes:
    - Clusterd index được lưu trữ như B-tree với node là index value, leaf lưu rows. Các rows được lưu trong bộ nhớ theo thứ tự của index.
    - Anvantages:
        + Các dữ liệu có liên quan được đặt gần nhau.
        + Lấy dự liệu nhanh do index và data cùng lưu trên B-tree.
        + Queries that use covering indexes can use the primary key values contained at the leaf node
    - Disavantages:
        + Nếu dữ liệu đã được lưu trong bộ nhớ theo thứ tự thì clustered index là không cần thiết.
        + Thao tác thêm, sửa, xóa dữ liệu có thể dẫn đến việc phải thay đổi thứ tự của row trong bộ nhớ.
        + Secondary index cần dùng 2 lần lockup index thay vì 1 lần.
    - Comparison of InnoDB and MyISAM data layout:
        + 
        + 

