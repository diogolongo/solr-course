# m4-11 Deleting Data

1. You can delete a single document using this command:

```
java -Ddata=args -Dc=psdemo -jar example\exampledocs\post.jar "<delete><id>scrum-development-jira-agile</id></delete>"
```

2. Or delete all the documents returned with a query:

```
java -Ddata=args -Dc=psdemo -jar example\exampledocs\post.jar '<delete><query>*:*</query></delete>'
```





