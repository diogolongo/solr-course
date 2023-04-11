# m5-15 Dismax & eDismax

1. Add Under the last `copyField`
```
<copyField source="coursetitle" dest="coursetitlesearch"/>
```

2. Then add under the `coursetitle` `field` tag.
```
<field name="coursetitlesearch" type="text_general" indexed="true" stored="true" multiValued="false"/> 
```

3. Reload the core.

4. In `q` write:
```
"Ben Sullins" jira
```

5. Select `edismax`

6. In `qf` write:
```
coursetitlesearch description course-author
```

7. In `qf` add:
```
coursetitlesearch description course-author^10.0
```

8. In `fl` write:
```
coursetitlesearch description course-author
```

9. In `qf` add:
```
coursetitlesearch^10.0 description course-author
```

10. Clear the query.

11. In `q` write:
```
jira agile scrum
```

12. In `fl` write:
```
coursetitlesearch releasedate
```

13. Select `edismax`

14. In `boost` write:
```
recip(ms(NOW,releasedate),3.16e-11,1,1)
```

