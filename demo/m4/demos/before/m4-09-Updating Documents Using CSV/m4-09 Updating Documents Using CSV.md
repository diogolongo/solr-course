# m4-09 Updating Documents Using CSV

1. Modify `Two sample courses with author.csv` by changing the `coursetitle` of the second document.

From:

```
Scrum Development with Jira & JIRA Agile
```

To:

```
Scrum Development with Xavier Morera
```

2. Copy `Two sample courses with author.csv` to ``solr-8.8.1\example\exampledocs\`

3. Index the document with `post.jar`

```
java -jar -Dc=psdemo -Dauto example\exampledocs\post.jar '.\example\exampledocs\Two sample courses with author.csv'
```

If you index content in this tutorial more than once, it will not duplicate the results found. The reason is that the schema (a file named either `managed-schema` or `schema.xml`) specifies a `uniqueKey` field called `id`. Whenever you POST commands to Solr to add a document with the same value for the `uniqueKey` as an existing document, it automatically updates the document.