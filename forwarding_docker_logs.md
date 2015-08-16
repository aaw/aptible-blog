---
title: Logging From Docker Containers
excerpt: "How Aptible manages logs from Docker containers"
author_name: Aaron Windsor
author_email: aaron@aptible.com
author_id: aaron
posted: 2015-08-19
section: Blog
posts: true
---

All apps and databases that run on Aptible's platform-as-a-service run as Docker
containers.

One of the first things you need once you have apps is logging. Our customers
used papertrail and logentries, but we wanted to give people a hosted solution
as well or ability to securely ship logs to someone they had a BAA with.

Explain how docker logs stdout/stderr from each container to a file here.

Briefly mention a few alternatives for logging with Docker, including Logstash.

We liked Logstash for a few reasons. First, we wanted something that
would allow our customers a lot of flexibility around how they process logs and
where they could send them. Logstash has a nice plugin system
for filters and outputs and an impressive number of open-source filter and output
implementations.
We also selfishly wanted to make use of Logstash's plugin ecosystem to
easily implement some basic push-button logging setups like an Elasticsearch
instance hosted on Aptible or a syslog output that sends logs to third-party log
management services like Papertrail or Logentries.
On top of all of that, many of our customers were already fans of the ELK stack
and liked using Kibana to explore logs.

The main problem with Logstash was that it didn't support syslog over TCP as an
output, describe our output implementation.

During prototyping, we quickly realized that Logstash was much too
resource-hungry to run ... logstash forwarder

We also realized that we wanted to run the logstash instances and the logstash
forwarders as Docker containers themselves...

Description of gentlemanjerry/joecool here, description of alpine for joecool.

Once in production, we realized a few more things: (1) memory cap on
gentlemanjerry (2) max line bytes for joecool.

End with full example of setting up logging to papertrail and logentries.