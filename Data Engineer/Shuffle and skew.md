___
- One partition has more data than other partition means heavy volume is mouduleated to one partition
- **how to tell** : whisker box plot , failing at 99%
- **way to deal with Skew** : 
 1.  Adaptive query execution-only in Spark 3+
	     Set spark.sql.adaptive.enabled = True
 2. Salting the GROUP BY - best option before Spark 3
     GROUP BY a random number, aggregate + GROUP BY again
     Be careful with things like AVG - break it into SUM and COUNT and divide!
	     df.withColumn("salt_random_column" (rand * n).cast(IntegerType))
	     .groupBylproupdyFlelds, "salt_randon_colum")
	     .agg (aggFields)
	     .groupBy(groupByFields)
	     .agg(aggFields)
