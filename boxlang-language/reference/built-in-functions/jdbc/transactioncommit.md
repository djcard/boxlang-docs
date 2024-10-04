# TransactionCommit

Commit the current transaction and persist all stored queries.

You can continue to use the transaction after a `transactionCommit()` call, but you will not be able to roll back past (before) this point since the changes are fully persisted to the database.

## Method Signature

```
TransactionCommit()
```

### Arguments

This function does not accept any arguments

## Examples

### Using TransactionCommit with TransactionRollback

This simple example shows two JDBC queries executed inside a transaction. The first query, an INSERT, is committed to the database while the second is rolled back.

```java
transaction {
    queryExecute( "INSERT INTO vehicles (id,make) VALUES (8, 'Ford' )", {}, { datasource : "carDB" } );
    transactionCommit();

    queryExecute( "UPDATE developers SET name = 'Chevrolet' WHERE id=8", {}, { datasource : "carDB" } );
    transactionRollback();
}
```

Note that the rollback cannot affect the INSERT statement, since it has already been committed ("persisted") to the database.

## Related

* [IsInTransaction](isintransaction.md)
* [IsWithinTransaction](iswithintransaction.md)
* [PreserveSingleQuotes](preservesinglequotes.md)
* [QueryExecute](queryexecute.md)
* [TransactionRollback](transactionrollback.md)
* [TransactionSetSavepoint](transactionsetsavepoint.md)