# DbMonitor for PHP
A Database Monitor for PHP

So here's the challenge... My PHP application, running on a cluster of PHP servers, needs to know
which database server to use in my cluster of database servers.
This isn't a new problem so it seems that there would be a proven, and open, solution, but I have
not found one.

* [mysqlnd_ms](https://pecl.php.net/package/mysqlnd_ms), or Sergio Tabnelli's
  [fork](https://github.com/sergiotabanelli/mysqlnd_ms) would seem like a good starting point but
  the failover options are extremely limited without another monitoring solution such as ClusterControl.
  This may be part of the solution, but it's not the entire solution.
* 
