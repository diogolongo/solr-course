# m4-17 DataImportHandler

NOTE: The DataImportHandler is deprecated as v8.6. See SOLR-14066 for more details. It is not shown in this training, however instructions are left for reference. 

1. In order to run this multi-core example, use the "-e" option in the bin/solr script:

```
.\bin\solr.cmd -e dih
```

2. When Solr starts, connect to: http://localhost:8983/solr/

* To import data from the hsqldb database, connect to:

  http://localhost:8983/solr/db/dataimport?command=full-import

* To import data from an ATOM feed, connect to:

  http://localhost:8983/solr/atom/dataimport?command=full-import

* To import data from your IMAP server:

  1. Edit the example-DIH/solr/mail/conf/mail-data-config.xml and add details about username, password, IMAP server
  2. Connect to http://localhost:8983/solr/mail/dataimport?command=full-import

* To copy data from db Solr core, connect to:

  http://localhost:8983/solr/solr/dataimport?command=full-import

* To index a full text document using Tika integration, connect to:

  http://localhost:8983/solr/tika/dataimport?command=full-import