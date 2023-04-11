# m4-18 Index all Sample Data

Prepare the core for the next chapter by indexing all the courses in Pluralsight (until 2014).

```
java -Durl="http://localhost:8983/solr/psdemo/update?f.tag.split=true&f.tag.separator=%20&f.tag.encapsulator='" -Dtype=text/csv -jar .\example\exampledocs\post.jar ".\example\exampledocs\All pluralsight courses with authors and tags.csv"
```


And then, let the `requestHandler` as it was before:

```
<requestHandler name="/select" class="solr.SearchHandler">
    <lst name="defaults">
      <str name="echoParams">explicit</str>
      <int name="rows">10</int>
    </lst>
</requestHandler>
```

