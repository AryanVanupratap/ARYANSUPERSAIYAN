Transaction Operations

- startTransaction() - starts a new transaction
- commitTransaction() - commits the transaction
- abortTransaction() - aborts the transaction
- withTransaction() - executes a function within a transaction

Transaction Options

- readConcern - specifies the read concern for the transaction
- writeConcern - specifies the write concern for the transaction
- readPreference - specifies the read preference for the transaction

Transaction Errors

- TransientTransactionError - a temporary error that can be retried
- UnknownTransactionCommitResult - the commit result is unknown
- TransactionAborted - the transaction was aborted