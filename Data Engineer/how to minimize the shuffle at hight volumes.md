___
 -  Bucket the data if multiple JOINs or aggregations are happening
  downstream
  - Spark has the ability to bucket data to minimize or eliminate the need for
  shuffle when doing JOINs
  - Bucket joins are very efficient but have drawbacks
  - Main drawback is the initial parallelism = number of buckets
  - Bucket joins only work if the two tables number of buckets are multiples оf
  each other!
 - Always use power of 2 for number of buckets