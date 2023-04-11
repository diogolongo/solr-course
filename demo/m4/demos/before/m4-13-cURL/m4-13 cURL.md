# m4-13 cURL

1. **Index** a document using cURL.

```
curl
url : http://localhost:8983/solr/psdemo/update?commit=true
content-type : text/xml
data : 
<add>
	<doc>
		<field name='courseid'>getting-started-enterprise-search-apache-solr</field>
		<field name='coursetitle'>Getting Started with Enterprise Search using Apache Solr</field>
	</doc>
</add>
```

Because you invoke the tool from the cmd, you will need to include everything without new lines:

```bash
curl.exe http://localhost:8983/solr/psdemo/update?commit=true -H "Content-Type: text/xml;" --data-binary "<add><doc><field name='courseid'>getting-started-enterprise-search-apache-solr</field><field name='coursetitle'>Getting Started with Enterprise Search using Apache Solr</field></doc></add>"
```

2. **Updating** a document using cURL,

```
curl
url : http://localhost:8983/solr/psdemo/update
content-type : text/json
data:
{
	'add':{ 
        'doc':{
            'courseid' : 'getting-started-enterprise-search-apache-solr',
            'coursetitle':{
                'set':'Updated using cURL and json'
            }
    	}
	}
}
```

Because you invoke the tool from the cmd, you will need to write everything without new lines:

```bash
curl.exe http://localhost:8983/solr/psdemo/update?commit=true -H "Content-Type: text/json;" --data-binary "{'add':{ 'doc':{'courseid':'getting-started-enterprise-search-apache-solr','coursetitle':{'set':'Updated using cURL and json'}}}}"
```

3. **Deleting** a document using cURL,

```
curl
http://localhost:8983/solr/psdemo/update?commit=true 
Content-Type: text/xml
data:
<delete>
	<id>getting-started-enterprise-search-apache-solr</id>
</delete>
```

Because you invoke the tool from the cmd, you will need to write everything without new lines:

```bash
curl.exe http://localhost:8983/solr/psdemo/update?commit=true -H "Content-Type: text/xml" --data-binary "<delete><id>getting-started-enterprise-search-apache-solr</id></delete>"
```