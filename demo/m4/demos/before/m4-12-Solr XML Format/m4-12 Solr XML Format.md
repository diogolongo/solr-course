# m4-12 Solr XML Format

1. Copy `solr-example-course.xml` to ``solr-8.8.1\example\exampledocs\`

2. Index the document with `post.jar`

```
java -jar -Dc=psdemo -Dauto example\exampledocs\post.jar ".\example\exampledocs\solr-example-course.xml"
```

