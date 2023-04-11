# m5-23 Request Handler

1. In `qt` write: `/pluralsight`

2. Add the following to `solr-4.7.0\example\solr\psdemo\conf\solrconfig.xml`

```
<requestHandler name="/pluralsight" class="solr.SearchHandler">
    <lst name="defaults">
        <str name="echoParams">explicit</str>
        <int name="rows">10</int>
        <str name="df">_text_</str>
        <str name="fl">courseid coursetitle releasedate iscourseretired courseauthor</str>
    </lst>
    <lst name="appends">
        <str name="fq">iscourseretired:no</str>
        <str name="facet">on</str>
        <str name="facet.field">course-author</str>
        <str name="facet.field">releasedate</str>
        <str name="facet.query">durationinseconds:[* TO 9999]</str>
        <str name="facet.query">durationinseconds:[10000 TO 19999]</str>
        <str name="facet.query">durationinseconds:[20000 TO 29999]</str>
        <str name="facet.query">durationinseconds:[30000 TO 39999]</str>
        <str name="facet.query">durationinseconds:[40000 TO 49999]</str>
        <str name="facet.query">durationinseconds:[50000 TO *]</str>
    </lst>
</requestHandler>
```

3. Go to the url:

http://localhost:8983/solr/psdemo/pluralsight?facet=on&q=*%3A*