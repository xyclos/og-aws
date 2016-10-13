#RDS
---

### RDS Basics

-	📒 [Homepage](https://aws.amazon.com/rds/) ∙ [User guide](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/) ∙ [FAQ](https://aws.amazon.com/rds/faqs/) ∙ [Pricing](https://aws.amazon.com/rds/pricing/)(see also [ec2instances.info/rds/](http://www.ec2instances.info/rds/)\)
-	**RDS** is a managed relational database service, allowing you to deploy and scale databases more easily. It supports Amazon Aurora, Oracle, Microsoft SQL Server, PostgreSQL, MySQL and MariaDB.

### RDS Tips

-	If you’re looking for the managed convenience of RDS for MongoDB, this isn’t offered by AWS directly, but you may wish to consider a provider such as [**mLab**](https://mlab.com/).
-	MySQL RDS allows access to [binary logs](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_LogAccess.Concepts.MySQL.html#USER_LogAccess.MySQL.BinaryFormat).
-	🔸**MySQL vs MariaDB vs Aurora:** If you prefer a MySQL-style database but are starting something new, you probably should consider Aurora and MariaDB as well. **Aurora** has increased availability and is the next-generation solution. That said, Aurora [may not be](http://blog.takipi.com/benchmarking-aurora-vs-mysql-is-amazons-new-db-really-5x-faster/) as fast relative to MySQL as is sometimes reported, and is more complex to administer. **MariaDB**, the modern [community fork](https://en.wikipedia.org/wiki/MariaDB) of MySQL, [likely now has the edge over MySQL](http://cloudacademy.com/blog/mariadb-vs-mysql-aws-rds/) for many purposes and is supported by RDS.
-	🔸**Aurora:** Aurora is based on MySQL 5.6. If you are planning to migrate to Aurora from an existing MySQL database, avoiding any MySQL features from 5.7 or later will ease the transition. The easiest migration path to Aurora is restoring a database snapshot from MySQL 5.6. The next easiest method is restoring a dump from a MySQL-compatible database such as MariaDB. If neither of those methods are options, Amazon offers a [fee-based data migration service](http://docs.aws.amazon.com/dms/latest/userguide/Welcome.html).

### RDS Gotchas and Limitations

-	⏱RDS instances run on EBS volumes, and hence are constrained by the EBS performance.
-	🔸Verify what database features you need, as not everything you might want is available on RDS. For example, if you are using Postgres, check the list of [supported features and extensions](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html#SQLServer.Concepts.General.FeatureSupport). If the features you need aren’t supported by RDS, you’ll have to deploy your database yourself.
-	🔸**DB migration to RDS:** While importing your database into RDS ensure you take into consideration the maintenance window settings. If a backup is running at the same time, your import can take a considerable longer time than you would have expected. 


