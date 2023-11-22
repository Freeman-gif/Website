Environment:
- Keep dependencies required by different project in separate places.
- Easily switch to an environment that requires different dependencies
Create an environment:
```
conda create --name myenv -y

conda create -f file.yml -n myenv # create an enviroment from yml file and name myenv

conda env update -f file.yml -n myenv # update myenv base on file.yml




conda activate env # activate the enviroment 

conda info --envs # check availbe envs

conda deactivate # deactivating the current environment and return to base environment

conda env remove --name myenv --all # remove the environment(after deactivate)


```

### MapReduce
Map-Reduce: Allow computations to be parallelized over a cluster. 
- Basic Map-Reduce
	- Distribution : Distribute the data.
	- Parallelism : Perform subsets of the computation simultaneously.
	- Fault Tolerance : Handle component failure.
	- The map-reduce framework plans task to run the correct partitions and shuffle data for the reduce function
	- Map: Apply a function to each data over a portion of data in parallel
	- Reduce: return one value from multiple values

Hadoop MapReduce vs. Spark
Extends the MapReduce model with primitives for efficient data sharing (Using Resilient Distributed Datasets (RDDs))
![[Pasted image 20231102214915.png]]


```
input = sc.textfile("../data...", 8),

rdd = sc.parallelize(data)
```
if just do input.collect(), it will return all the entire data in a list 
do input.glom().collect()
```

RDD operations;
Two types  
◦ Transformation  
	◦ Perform functions against each element in an RDD and return a new RDD.  Construct a new RDD from an existing RDD,Doesn’t change the original RDDs
		```
		splitted_input_rdd = input_rdd.map(lambda x :x.split('\t')
```

	◦ Lazy evaluation – operations are only evaluated when an action is requested.  
◦ Action  
	◦ Trigger a computation and return a value to the Spark driver.  
