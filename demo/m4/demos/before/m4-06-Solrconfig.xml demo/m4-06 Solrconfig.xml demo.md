# m4-06 Solrconfig.xml demo

1. Make following changes to `solr-8.8.1\server\solr\psdemo\conf\solrconfig.xml`

From:

```
<requestHandler name="/select" class="solr.SearchHandler">
    <!-- default values for query parameters can be specified, these
         will be overridden by parameters in the request
      -->
    <lst name="defaults">
      <str name="echoParams">explicit</str>
      <int name="rows">10</int>
      <!-- Default search field
         <str name="df">text</str> 
        -->
      <!-- Change from JSON to XML format (the default prior to Solr 7.0)
         <str name="wt">xml</str> 
        -->
    </lst>
...
```

To:

```
<str name="df">_text_</str>
<str name="wt">xml</str>
<str name="indent">true</str>
<str name="facet">on</str>
<str name="facet.field">course-author</str>
```

2. Reload the core.

3. Copy `Two sample courses with author.csv` to ``solr-8.8.1\example\exampledocs\`

4. Index the document with `post.jar`

```
java -jar -Dc=psdemo -Dauto example\exampledocs\post.jar '.\example\exampledocs\Two sample courses with author.csv'
```

