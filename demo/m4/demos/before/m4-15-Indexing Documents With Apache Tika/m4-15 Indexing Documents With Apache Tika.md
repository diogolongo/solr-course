# m4-15 Indexing Documents With Apache Tika

1. Create a new core called `pstika`

```
bin\solr.cmd create -c pstika
```

2. Add these libraries to `solr-8.8.1\server\solr\pstika\conf\solrconfig.xml`

```
<lib dir="${solr.install.dir:../../..}/contrib/extraction/lib" regex=".*\.jar" />
<lib dir="${solr.install.dir:../../..}/dist/" regex="solr-cell-\d.*\.jar" />
```

3. Add a new `requestHandler` to `solr-8.8.1\server\solr\pstika\conf\solrconfig.xml` 

```
<requestHandler name="/update/extract" startup="lazy" class="solr.extraction.ExtractingRequestHandler" >
    <lst name="defaults">
        <str name="lowernames">true</str>
        <str name="fmap.content">_text_</str>
    </lst>
</requestHandler>
```

4. Then, post the file using `curl` or `post.cmd`

```
curl.exe "http://localhost:8983/solr/pstika/update/extract?literal.id=doc1&commit=true" -F "myfile=@example/exampledocs/solr-word.pdf"
```

