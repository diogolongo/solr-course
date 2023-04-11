# m3-03 Install, Run, Index and Query

**Download it**: download Solr from:

```
https://solr.apache.org/downloads.html
```

**Move it**: Let's move the `.zip` file to the directory where you want to store it , for example `C:\pluralsight-solr`.

**Run it**: Follow these steps in order to start solr:

1. Unzip it.

```
unzip -q solr-8.8.0.zip
cd solr-8.8.0/
```

You can check [here](https://solr.apache.org/guide/8_8/installing-solr.html#directory-layout) to see the new solr directory layout!

2. Start solr.

```
bin\solr.cmd start 
```

3. When the command prompt indicate you to open a browser navigate to: `http://localhost:8983/solr`. When the solr UI loads our server is up and running! 

4. Create our first core

```
# bin\solr create -c <corename>
# bin\solr create -help

bin\solr.cmd create -c techproducts -d sample_techproducts_configs
```

The option `sample_techproducts_configs` is provided in order to work with the samples already included, but if not specified the default to use is: `_default`

Source: [Installing Solr](https://solr.apache.org/guide/8_8/installing-solr.html)

The core could be located in: 

```
D:\solr-8.8.1\server\solr\techproducts
```

5. Index the Techproducts Data

```
java -jar -Dc=techproducts -Dauto example\exampledocs\post.jar example\exampledocs\*
```

6. If you want to stop the server, you can do it with:

```
.\bin\solr.cmd stop -p 8983
```

7. You can always use `-help` to get more information about the command line options:

```
.\bin\solr.cmd -help
.\bin\solr.cmd start -help
.\bin\solr.cmd stop -help
```

8. Also, you can start solr in another port using:

```
.\bin\solr.cmd start -p 8983
```