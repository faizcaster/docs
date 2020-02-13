<span class="version-tag">New in v20.1</span>: The `SELECT FOR UPDATE` statement is used to order transactions by controlling concurrent access to one or more rows of a table. It causes the rows returned by a [selection query][selection] to be effectively "locked", such that other transactions trying to access those rows are forced to wait for the first transaction to finish. These other transactions are effectively put into a queue based on when they tried to read the value of the locked row(s).

Benefits of using `SELECT FOR UPDATE` include:

- Reduced [transaction contention][transaction_contention] when your workload requires concurrent access to the same rows.
- Increased throughput.
- Decreased latency (especially tail latency).
- A substantial reduction the number of [transaction retries][retries] in scenarios where a transaction performs a read and then updates the same row it just read.

<!-- Reference Links -->

[transaction_contention]: performance-best-practices-overview.html#understanding-and-avoiding-transaction-contention
[retries]: transactions.html#transaction-retries
[select]: select-clause.html
[selection]: selection-queries.html
