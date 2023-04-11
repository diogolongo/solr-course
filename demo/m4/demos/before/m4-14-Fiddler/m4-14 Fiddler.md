# m4-14 Fiddler

1. Create a Request using **Fiddler** with the following values:

```
url: 

	http://localhost:8983/solr/psdemo/update?wt=json&commit=true
	
Headers:

	Content-Type: application/json
	
Body:

{
  "add": {
    "doc": {
      "courseid": "getting-started-enterprise-search-apache-solr",
      "coursetitle": {
        "set": "Updated using Fiddler and json"
      }
    }
  }
}
```

2. Lets update the course title with another request in fiddler:

```
url: 

	http://localhost:8983/solr/psdemo/update?wt=json&commit=true
	
Headers:

	Content-Type = application/json
	
Body:

{
  "add": {
    "doc": {
      "courseid": "getting-started-enterprise-search-apache-solr",
      "coursetitle": {
        "set": "Updated using Fiddler and then modified"
      }
    }
  }
}
```

