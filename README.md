# DbMonitor for PHP
A Database Monitor for PHP

So here's the challenge... My PHP application, running on a cluster of PHP servers, needs to know
which database server to use in my cluster of database servers.
This isn't a new problem so it seems that there would be a proven, and open, solution, but I have
not found one.

* [mysqlnd_ms](https://pecl.php.net/package/mysqlnd_ms), or Sergio Tabnelli's
  [fork](https://github.com/sergiotabanelli/mysqlnd_ms), would seem like a good starting point but
  the failover options are extremely limited without another monitoring solution such as ClusterControl.
  This may be part of the solution, but it's not the entire solution.
* [MariaDB MaxScale](https://mariadb.com/kb/en/maxscale/) provides a proxy and monitor that works pretty
  well, but the Business Source License limits the user to "less than three" databases without a paid license.
* [ProxySQL](https://proxysql.com/) provides an insanely fast proxy, but it needs a monitoring solution to
  handle failover. The ProxySQL HA documenation mentions MHA (Master High Availability Manager and tools for MySQL),
  but I cannot find any indication that it is still being developed.
* [orchestrator](https://github.com/openark/orchestrator) was a very nice high availability and replication
  management tool, but it is no longer being maintained.

Suggesting that a database monitor could/should be built in PHP is certain to generate some eye rolls.
MaxScale is written in C++, ProxySQL in C and I believe orchestrator is in Go.
But, I believe it's possible and that there are valid reasons to make the effort.
* A PHP based monitor sees databases the same way PHP does, if the monitor cannot connet then PHP won't be
  able to connect.
* A PHP based monitor can get hints from application state, such as user sessions, so it's more obvious when
  there is an immediate read after a write.
* While PHP's interprocess communications are quite limited, a php based solution will have access to the same
  resources and hopefully provide a cleaner path for integration.
* And most important to me, the functionality is clear and open so it's clear exactly what is happening.

And with that, the effort begins.

