# 3. Solr Configuration Demos

## m3-02 Getting Solr and Overview

**Download it**: Download Solr from:

```
https://solr.apache.org/downloads.html
```

**Run it**

1. Unzip it.

```
unzip -q solr-8.8.0.zip
cd solr-8.8.0/
```

You can check [here](https://solr.apache.org/guide/8_8/installing-solr.html#directory-layout) to see the new solr directory layout!

2. Start Solr.

```
bin\solr.cmd start 
```

3. Create our first core.

```
# bin/solr create -c <corename>
# bin/solr create -help

bin\solr.cmd create -c techproducts -d sample_techproducts_configs
```

The option `sample_techproducts_configs` is provided in order to work with the samples already included, but if not specified, default option is: `_default`

Source: [Installing Solr](https://solr.apache.org/guide/8_8/installing-solr.html)

The core is located: 

```
D:\solr-8.8.1\server\solr\techproducts
```

4. Index the Techproducts Data

```
java -jar -Dc=techproducts -Dauto example\exampledocs\post.jar example\exampledocs\*
```

