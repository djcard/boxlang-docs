# QueryDeleteRow

This function deletes a row from the query

## Method Signature

```
QueryDeleteRow(query=[query], row=[integer])
```

### Arguments

| Argument   | Type      | Required   | Description                      | Default   |
| ---------- | --------- | ---------- | -------------------------------- | --------- |
| `query`    | `query`   | `true`     | The query to delete the row from |           |
| `row`      | `integer` | `true`     | The row index to delete          |           |
| ---------- | ------    | ---------- | -------------                    | --------- |

## Examples

```
QueryDeleteRow(query=[query], row=[integer])
```

## Related

* [QueryAddColumn](queryaddcolumn.md)
* [QueryAddRow](queryaddrow.md)
* [QueryAppend](queryappend.md)
* [QueryClear](queryclear.md)
* [QueryColumnArray](querycolumnarray.md)
* [QueryColumnCount](querycolumncount.md)
* [QueryColumnData](querycolumndata.md)
* [QueryColumnExists](querycolumnexists.md)
* [QueryCurrentRow](querycurrentrow.md)
* [QueryDeleteColumn](querydeletecolumn.md)
* [QueryEach](queryeach.md)
* [QueryEvery](queryevery.md)
* [QueryFilter](queryfilter.md)
* [QueryGetCell](querygetcell.md)
* [QueryGetResult](querygetresult.md)
* [QueryKeyExists](querykeyexists.md)
* [QueryMap](querymap.md)
* [QueryNew](querynew.md)
* [QueryPrepend](queryprepend.md)
* [QueryRecordCount](queryrecordcount.md)
* [QueryReduce](queryreduce.md)
* [QueryRowData](queryrowdata.md)
* [QuerySetCell](querysetcell.md)
* [QuerySetRow](querysetrow.md)
* [QuerySlice](queryslice.md)
* [QuerySome](querysome.md)
* [QuerySort](querysort.md)