# QueryStringToStruct

Convert a query string to a struct.

Each key-value pair in the query string is separated by a delimiter. The default delimiter is ,{@code "&"}, ,

, Example:

,

```
,
queryStringToStruct( "foo=bar,&,baz=qux" );
"foo=bar,&,baz=qux".toStruct();
,
```

## Method Signature

```
QueryStringToStruct(target=[string], delimiter=[string])
```

### Arguments

| Argument    | Type     | Required | Description                                                         | Default |
| ----------- | -------- | -------- | ------------------------------------------------------------------- | ------- |
| `target`    | `string` | `true`   | The query string to convert.                                        |         |
| `delimiter` | `string` | `false`  | The delimiter used to separate key-value pairs in the query string. | `&`     |

## Examples

## Related

* [Ascii](ascii.md)
* [CamelCase](camelcase.md)
* [Char](char.md)
* [CharsetDecode](charsetdecode.md)
* [CharsetEncode](charsetencode.md)
* [Compare](compare.md)
* [CompareNoCase](comparenocase.md)
* [Find](find.md)
* [FindNoCase](findnocase.md)
* [FindOneOf](findoneof.md)
* [Insert](insert.md)
* [JSStringFormat](jsstringformat.md)
* [KebabCase](kebabcase.md)
* [LCase](lcase.md)
* [Left](left.md)
* [ListReduce](listreduce.md)
* [LJustify](ljustify.md)
* [LTrim](ltrim.md)
* [Mid](mid.md)
* [ParagraphFormat](paragraphformat.md)
* [PascalCase](pascalcase.md)
* [ReEscape](reescape.md)
* [ReFind](refind.md)
* [reFindNoCase](refindnocase.md)
* [ReMatch](rematch.md)
* [reMatchNoCase](rematchnocase.md)
* [RemoveChars](removechars.md)
* [RepeatString](repeatstring.md)
* [Replace](replace.md)
* [ReplaceList](replacelist.md)
* [ReplaceListNoCase](replacelistnocase.md)
* [ReplaceNoCase](replacenocase.md)
* [ReReplace](rereplace.md)
* [reReplaceNoCase](rereplacenocase.md)
* [Reverse](reverse.md)
* [Right](right.md)
* [RJustify](rjustify.md)
* [RTrim](rtrim.md)
* [Slugify](slugify.md)
* [SnakeCase](snakecase.md)
* [SpanExcluding](spanexcluding.md)
* [SpanIncluding](spanincluding.md)
* [SQLPrettify](sqlprettify.md)
* [StringBind](stringbind.md)
* [StringEach](stringeach.md)
* [StringEvery](stringevery.md)
* [StringFilter](stringfilter.md)
* [StringMap](stringmap.md)
* [StringReduce](stringreduce.md)
* [StringReduceRight](stringreduceright.md)
* [StringSome](stringsome.md)
* [StringSort](stringsort.md)
* [StripCR](stripcr.md)
* [Trim](trim.md)
* [TrueFalseFormat](truefalseformat.md)
* [UCase](ucase.md)
* [UCFirst](ucfirst.md)
* [Val](val.md)
* [Wrap](wrap.md)
* [YesNoFormat](yesnoformat.md)