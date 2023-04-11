# m4-06 Schema.xml demo

1. Create the core.

```
bin\solr.cmd create -c pscollection
```

2. Rename `solr-8.8.1\server\solr\pscollection\conf\managed-schema` to `solr-8.8.1\server\solr\pscollection\conf\schema.xml`

3. Add the following text to `solr-8.8.1\server\solr\pscollection\conf\solrconfig.xml` under the `directoryFactory` tag:

```
<schemaFactory class="ClassicIndexSchemaFactory"/>
```

4. **Delete** everything in `updateProcessor` and `updateRequestProcessorChain` tags.

```
  <updateProcessor class="solr.UUIDUpdateProcessorFactory" name="uuid"/>
  <updateProcessor class="solr.RemoveBlankFieldUpdateProcessorFactory" name="remove-blank"/>
  <updateProcessor class="solr.FieldNameMutatingUpdateProcessorFactory" name="field-name-mutating">
    <str name="pattern">[^\w-\.]</str>
    <str name="replacement">_</str>
  </updateProcessor>
  <updateProcessor class="solr.ParseBooleanFieldUpdateProcessorFactory" name="parse-boolean"/>
  <updateProcessor class="solr.ParseLongFieldUpdateProcessorFactory" name="parse-long"/>
  <updateProcessor class="solr.ParseDoubleFieldUpdateProcessorFactory" name="parse-double"/>
  <updateProcessor class="solr.ParseDateFieldUpdateProcessorFactory" name="parse-date">
    <arr name="format">
      <str>yyyy-MM-dd['T'[HH:mm[:ss[.SSS]][z</str>
      <str>yyyy-MM-dd['T'[HH:mm[:ss[,SSS]][z</str>
      <str>yyyy-MM-dd HH:mm[:ss[.SSS]][z</str>
      <str>yyyy-MM-dd HH:mm[:ss[,SSS]][z</str>
      <str>[EEE, ]dd MMM yyyy HH:mm[:ss] z</str>
      <str>EEEE, dd-MMM-yy HH:mm:ss z</str>
      <str>EEE MMM ppd HH:mm:ss [z ]yyyy</str>
    </arr>
  </updateProcessor>
  <updateProcessor class="solr.AddSchemaFieldsUpdateProcessorFactory" name="add-schema-fields">
    <lst name="typeMapping">
      <str name="valueClass">java.lang.String</str>
      <str name="fieldType">text_general</str>
      <lst name="copyField">
        <str name="dest">*_str</str>
        <int name="maxChars">256</int>
      </lst>
      <!-- Use as default mapping instead of defaultFieldType -->
      <bool name="default">true</bool>
    </lst>
    <lst name="typeMapping">
      <str name="valueClass">java.lang.Boolean</str>
      <str name="fieldType">booleans</str>
    </lst>
    <lst name="typeMapping">
      <str name="valueClass">java.util.Date</str>
      <str name="fieldType">pdates</str>
    </lst>
    <lst name="typeMapping">
      <str name="valueClass">java.lang.Long</str>
      <str name="valueClass">java.lang.Integer</str>
      <str name="fieldType">plongs</str>
    </lst>
    <lst name="typeMapping">
      <str name="valueClass">java.lang.Number</str>
      <str name="fieldType">pdoubles</str>
    </lst>
  </updateProcessor>

  <!-- The update.autoCreateFields property can be turned to false to disable schemaless mode -->
  <updateRequestProcessorChain name="add-unknown-fields-to-the-schema" default="${update.autoCreateFields:true}"
           processor="uuid,remove-blank,field-name-mutating,parse-boolean,parse-long,parse-double,parse-date,add-schema-fields">
    <processor class="solr.LogUpdateProcessorFactory"/>
    <processor class="solr.DistributedUpdateProcessorFactory"/>
    <processor class="solr.RunUpdateProcessorFactory"/>
  </updateRequestProcessorChain>
```

5. Make the following changes in the  `solr-8.8.1\server\solr\pscollection\conf\schema.xml` document:

**Add fields**

From:

```
<field name="id" type="string" indexed="true" stored="true" required="true" multiValued="false" />
```

To:

```
<field name="courseid" type="string" indexed="true" stored="true" required="true" multiValued="false" />
<!--pscollection fields-->
<field name="coursetitle" type="string" indexed="true" stored="true" multiValued="false"/>   
<field name="durationinseconds" type="pint" indexed="true" stored="true" />  
<field name="releasedate" type="pdate" indexed="true" stored="true"/>
<field name="description" type="text_general" indexed="true" stored="true"/>
<field name="assessmentstatus" type="string" indexed="true" stored="true"/> 
<field name="iscourseretired" type="string" indexed="true" stored="true"/>  
<field name="tag" type="string" multiValued="true" indexed="true" stored="true"/>
<!--end pscollection fields-->
```

**Change the uniqueKey**

From:

```
<uniqueKey>id</uniqueKey>
```

To:

```
<uniqueKey>courseid</uniqueKey>
```

**Add copyField tags**

Add:

```
<copyField source="coursetitle" dest="_text_"/>
<copyField source="description" dest="_text_"/>
```

Under the `uniqueKey` tag

3. Reload the core.

4. Duplicate the `pscollection` core, copy the entire `solr-8.8.1\server\solr\pscollection` and rename it to: `solr-8.8.1\server\solr\psdemo`
5. Also rename the file `solr-8.8.1\server\solr\pscollection\core.properties`

```
name=psdemo
```

6. Add: 

```
<field name="course-author" type="string" multiValued="true" indexed="true" stored="true" /> 
```

To `solr-8.8.1\server\solr\psdemo\conf\schema.xml`

7. Restart the Solr server.

```
bin\solr.cmd restart -p 8983
```

