---
title: "Set up SSL for SolrCloud"
date: 2022-08-24
author: "Me"
draft: false
---

As I am highly dependent on official documentation, I found that Apache Solr maintain an awesome documentation from which I learned a lot. Setting up SSL can be found [here](https://solr.apache.org/guide/solr/latest/deployment-guide/enabling-ssl.html). I am writing this for easier step by step setup.

Happy Searching!

# Generate certificate & key

From the official documentation, you can generate a self-signed certificate to test your setup. But for the trusted authority, generate a certificate and convert it to `.pfx` format, which is type `PKCS12`.

And before starting Solr, we need to configure zookeeper.

# Configure Zookeeper

We must configure Solr cluster properties in Zookeeper so that Solr nodes know to communicate via SSL. After creating, setting up and starting Zookeeper, we need to setup `urlScheme` cluster-wide property to `https` before any Solr nodes start up.

For *Unix*, go to `$solr_home` and run,

```bash
server/scripts/cloud-scripts/zkcli.sh -zkhost server1:2181,server2:2181,server3:2181 -cmd clusterprop -name urlScheme -val https
```

For existing collections, we can update cluster properties by using the Collections API (*CLUSTERPROP*):

```bash
http://IP:8983/solr/admin/collections?action=CLUSTERPROP&name=urlScheme&val=https
```

This command only needs to be run on one node of the cluster, the change will apply to all nodes.

# Configure Solr

At this point, I think we all have set up zookeeper properly, have certificates and key at hand and didn't start Solr. Now, let's set up system properties of Solr in `$solr_home/bin/solr.in.sh` or, `/etc/default/solr.in.sh`:

```bash
SOLR_SSL_ENABLED=true
SOLR_SSL_KEY_STORE=/etc/solr-ssl.keystore.p12    # define your store path
SOLR_SSL_KEY_STORE_PASSWORD=secret    # use your store password
SOLR_SSL_TRUST_STORE=/etc/solr-ssl.keystore.p12    # define your store path
SOLR_SSL_TRUST_STORE_PASSWORD=secret    # use your store password
SOLR_SSL_NEED_CLIENT_AUTH=false
SOLR_SSL_WANT_CLIENT_AUTH=false
SOLR_SSL_CHECK_PEER_NAME=true
```

Now, start Solr and it's working.

If you use curl, see the official documentation section on how to use curl in case of SSL.


