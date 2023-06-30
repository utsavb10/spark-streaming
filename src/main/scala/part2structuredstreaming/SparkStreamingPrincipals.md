# Spark Architecture

applications                    Streaming   ML  GraphX  OtherLibraries
high level(structured) APIs     DataFrames    Datasets    SparkSQL
low level APIs                  DStream     RDDs    Distributed Variables

# Why

Once we compute something valuable, we want something updates<br>
We need continuous big data processing -> Spark Streaming<br>

# Stream Processing

<li> Include new data to compute result
<li> No definitive end of incoming data
<li> Batch Processing = operate on a big data set, compute result once </li>

In practice, stream and batch interoperate
<li> incoming data joined with a fixed dataset</li>
<li> output of a streaming job queried by a batch job</li>
<li> consistency between batch/streaming jobs (ed bank account balance)</li>

### Real Time Example
<ul>
<li> sensor reading </li>
<li> interaction with an application/website</li>
<li> credit card transactions</li>
<li> real-time dashboards</li>
<li> alerts and notifications</li>
<li> incremental big data</li>
<Li> incremental transactional data eg analytics or accounts</Li>
<li> incremental machine learning</li>
</ul>

### Pros

<li>Much lower latency than batch processing</li>
<li> Greater performance/latency</li>


### Difficulties
<li> Maintaining state and order for incoming data (event time processing) </li>
<li> Exactly once processing in the context of machine failures (fault tolerance)</li>
<li> Responding to events at low latency</li>
<li> Transaction data at runtime</li>
<li> Updating business logic at runtime</li>

## Spark Streaming Principles
Spark Streaming operated on micro-batches

#### Declarative API
- Write "what" needs to be computed, let the library decide "how"<br>
- Alternative: RaaT (record-at-a-time)
  - set of APIs to process each incoming event as it arrives
  - low-level: maintaining state & resource usage is your responsibility
  - hard to develop

#### Event time vs Processing time API
- event time = when the event was produced
- processing time = when the event was processed
- event time is critical: allows detection of late data points (something related to watermarks)

#### Continuous vs micro-batch execution
- continuous = include each data point as it arrives (lower latency)
- micro-batch = wait for a few data points, process them all in the new result (higher throughput)
    
    