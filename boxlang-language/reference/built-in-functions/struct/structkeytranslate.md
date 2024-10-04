# StructKeyTranslate

Converts a struct with dot-notated keys in to an unflattened version

## Method Signature

```
StructKeyTranslate(struct=[structloose], deep=[boolean], retainKeys=[boolean])
```

### Arguments

| Argument     | Type      | Required | Description                                                     | Default |
| ------------ | --------- | -------- | --------------------------------------------------------------- | ------- |
| `struct`     | `struct`  | `true`   | The struct to unflatten                                         |         |
| `deep`       | `boolean` | `false`  | Whether to recurse in to nested keys - default false            | `false` |
| `retainKeys` | `boolean` | `false`  | Whether to retain the original dot-notated keys - default false | `false` |

## Examples

## Related

* [StructAppend](structappend.md)
* [StructClear](structclear.md)
* [StructCopy](structcopy.md)
* [StructDelete](structdelete.md)
* [StructEach](structeach.md)
* [StructEquals](structequals.md)
* [StructEvery](structevery.md)
* [StructFilter](structfilter.md)
* [StructFind](structfind.md)
* [StructFindKey](structfindkey.md)
* [StructFindValue](structfindvalue.md)
* [StructGet](structget.md)
* [StructGetMetadata](structgetmetadata.md)
* [StructInsert](structinsert.md)
* [StructIsCaseSensitive](structiscasesensitive.md)
* [StructIsOrdered](structisordered.md)
* [StructKeyArray](structkeyarray.md)
* [StructKeyExists](structkeyexists.md)
* [StructKeyList](structkeylist.md)
* [StructMap](structmap.md)
* [StructNew](structnew.md)
* [StructReduce](structreduce.md)
* [StructSome](structsome.md)
* [StructSort](structsort.md)
* [StructToQueryString](structtoquerystring.md)
* [StructToSorted](structtosorted.md)
* [StructUpdate](structupdate.md)
* [StructValueArray](structvaluearray.md)