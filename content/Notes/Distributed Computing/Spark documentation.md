MapReduce:
- allow computations to be parallelized over a cluster
- basic map-reduce
- the map_recue framework plans map tasks to be run on the correct partitions and shuffle data for the reduce function
- Map:
	- Apply a function to each data over a portion of data in parallel 

```

map (mapping data to cpu (workers))
```
Lambda function:
```
lambda x :  x + 2
```

##### Check the number of partitions 
```
rdd. getNumPartitions()
```

##### initialize 
```
sc.textFile("file", number of partitions)
```
```
sc.parallize(list/array, numbner of partitions)
```

##### Transformation 
- Perform functions against each element in an RDD and return a new RDD
	- Construct a new RDD from existing RDD
		- Doesn't change the original RDD
	- changing the data structure to sth new RDD
	- Narrow Transformation:
		- Transform data without any shuffles( only interact with each partitions )
	- Wide Transformation:
		- when the operations may require data shuffling(look through the whole partitions )
- lazy evaluation  operations are evaluated when an action is requested
	- track how many transformations happen 
	- 

map(function):
```

```


##### Action:
	- Trigger a computation and return a value to the Spark driver 
	- Aggregate (zeroValue, seqOp, combOp)
	- fold


#### Paire RDDs:


- key value pairs commonly used for many operations including aggtegations, ETL(Extract, transform and upload) in Spark
- Allow operations on each key in parallel or regroup data across the network such as reduceBykey(), etc 

Create pair RDD, 
map (lambda x: x.split(',')) => RDD
key: could be a simple object(integer , string, etc. ) to complex objects (tuple, etc.)
Value: could be a simple objects to data structures (lists, tuples, dictionarier, set, etc . )



Load 

map(lambda X: [ int(x[0],x[1])])



Operations in Pair RDDs:



 - Transformations;
	 - keyes() -- return an RDD of just the keys
	 - values() - return an RDD of just the values
	 - sortByKey() - return an RDD sorted by the key
	 - groupbykey()
		 - group data use the key
		 - Return an RDD of (key, Resultlterable) pairs --shuffle
	- MapValues(func)
		- Pass each value in the key value pair RDD through a map function without changing the keys
		- Retain the original RDD's partitioning 
	- flattern key and value 
		- flatMapValues (func) -- shuffle
		- flat each key value pair RDD through a flatmap function without changing the keys
		- Retain the originial RDD's partitioning 

		- Reduce(lambda: x, y : x+y) --shuffle
	- sortBy() -shuffle the data
	- reduceby() will always faster than groupby() because it doesn't require reshuffle 
- Actions:
	- countByKey()
		- Count the number of elements for each key
	-  lookup(key)
		- 

			
