# ListLen

Calculates the length of a list separated by the specified delimiter

## Method Signature

```
ListLen(list=[string], delimiter=[string], includeEmptyFields=[boolean])
```

### Arguments

| Argument             | Type      | Required   | Description                                                    | Default   |
| -------------------- | --------- | ---------- | -------------------------------------------------------------- | --------- |
| `list`               | `string`  | `true`     | string list to calculate the length                            |           |
| `delimiter`          | `string`  | `false`    | string the list delimiter                                      | ,         |
| `includeEmptyFields` | `boolean` | `false`    | boolean whether to include empty fields in the returned result | false     |
| ----------           | ------    | ---------- | -------------                                                  | --------- |

## Examples

```
ListLen(list=[string], delimiter=[string], includeEmptyFields=[boolean])
```

## Related

* [GetToken](gettoken.md)
* [ListAppend](listappend.md)
* [ListAvg](listavg.md)
* [ListChangeDelims](listchangedelims.md)
* [ListCompact](listcompact.md)
* [ListContains](listcontains.md)
* [ListContainsNoCase](listcontainsnocase.md)
* [ListDeleteAt](listdeleteat.md)
* [ListEach](listeach.md)
* [ListEvery](listevery.md)
* [ListFilter](listfilter.md)
* [ListFind](listfind.md)
* [ListFindNoCase](listfindnocase.md)
* [ListFirst](listfirst.md)
* [ListGetAt](listgetat.md)
* [ListIndexExists](listindexexists.md)
* [ListInsertAt](listinsertat.md)
* [ListItemTrim](listitemtrim.md)
* [ListLast](listlast.md)
* [ListMap](listmap.md)
* [ListPrepend](listprepend.md)
* [ListQualify](listqualify.md)
* [ListReduceRight](listreduceright.md)
* [ListRemoveDuplicates](listremoveduplicates.md)
* [ListRest](listrest.md)
* [ListSetAt](listsetat.md)
* [ListSome](listsome.md)
* [ListSort](listsort.md)
* [ListToArray](listtoarray.md)
* [ListTrim](listtrim.md)
* [ListValueCount](listvaluecount.md)
* [ListValueCountNoCase](listvaluecountnocase.md)