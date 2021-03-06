---
title: Run interlock on Carina
author: Kyle Kelley <kyle.kelley@rackspace.com>
date: 2015-10-15
permalink: docs/tutorials/interlock-on-carina/
description: Use interlock to load balance containers or emit statistics across your Swarm cluster
topics:
  - docker
  - interlock
  - events
  - intermediate
---

This tutorial describes [interlock](https://github.com/ehazlett/interlock), which you can use to load balance your containers across a Carina cluster, send statistics to Carbon, or perform other Carina event-driven operations.

### Prerequisites

* [Create and connect to a cluster](/docs/tutorials/create-connect-cluster/) named `boatie`
* Your API Key. Go to the [Carina control panel](https://app.getcarina.com), click your username in the top-right corner, and then click **API Key**.

### Interlock

Interlock listens for new Docker events, such as a new container being started, and, according to your configuration, notifies plug-ins.

Interlock has plug-ins for:

* Load balancing via HAProxy
* Load balancing via NGINX
* Statistics forwarding to Carbon

Normally for interlock you need to mount a volume with certificates, set TLS options, and optionally set environment variables. Using [libcarina](https://github.com/getcarina/libcarina), the go bindings for Carina, interlock in Carina has been modified to require only your username, API key, and the name of the cluster you want to run on.

### Run an interlock container

Run an interlock container that uses the `example` plug-in to simply echo that an event has been received.

```bash
$ docker run carina/interlock --username $USERNAME  --api-key $APIKEY --clustername boatie --plugin example start
time="2015-10-19T01:22:59Z" level=info msg="interlock running version=0.3.2 (2df2d23)"
time="2015-10-19T01:22:59Z" level=info msg="loading plugin name=example version=0.1"
time="2015-10-19T01:22:59Z" level=info msg="[interlock] dispatching event to plugin: name=example version=0.1"
time="2015-10-19T01:22:59Z" level=info msg="[example] action=received event= time=1445217779076879776"
```

### Troubleshooting

See [Troubleshooting common problems](/docs/tutorials/troubleshooting/).

For additional assistance, ask the [community](https://community.getcarina.com/) for help or join us in IRC at [#carina on Freenode](http://webchat.freenode.net/?channels=carina).

### Resources

* The [Carina Interlock project](https://github.com/getcarina/interlock)
* [libcarina](https://github.com/getcarina/libcarina)

### Next step

Run your first containerized application by [getting started on Carina](/docs/getting-started/getting-started-on-carina/).

<!--
TODO: Use the text below when that tutorial is back in for M2.

See Interlock in action in the [Load balance WordPress in Docker containers](/docs/tutorials/load-balance-wordpress-docker-containers/) tutorial
-->
