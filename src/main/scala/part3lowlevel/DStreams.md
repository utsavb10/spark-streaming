# DStreams
Discretized Streams

## What ? 
Never ending sequence of RDDs
- nodes' clocks are synchronized
- batches are triggered at the same time in the cluster
- each batch is an RDD

Essentially a distributed collection of elements of the same type
- functional operators eg map, flatMap, filter, reduce
- accessors to each RDD
- more advanced operators (later)

Needs a <u>receiver</u> to perform computations
- one receiver per DStream
- fetches data from the source, sends to Spark, creates block
- is managed by the StreamingContext on the driver
- occupies one core on the machine