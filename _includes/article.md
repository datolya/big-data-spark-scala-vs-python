📊 April 4th, 2025 
📝 authored by Sebestyén Gergely 

It is not really a *modern* skill, to process all available information and come up with a reasonable plan of action. 

It is interesting to consider, then, what it exactly means that we're living in an information economy, and why data professionals are sought after in almost every conceivable business domain. 
What seems to have fundamentally changed is the toolkit we're now required to adopt, in order to successfully observe everything we know and generate practical value from it. 

Nowadays, firms tend to regard data as a first-class citizen and the backbone of well-calculated business decisions. We're relying on increasingly sophisticated computing resources just to make sense of large (and growing) information streams. 
Data professionals are accustomed to working at scale, to the point where the term <span style="font-weight: 400;">Big Data</span> is not that meaningful to distinguish the architecture of one company from that of another.

So why, then, is the term still mainstream? Why was <span style="font-weight: 400;">Big Data</span> ever relevant in the first place?  

## Beyond a Buzzword: What Is Big Data?

Let's try to understand this in layman terms. We want to map out the origins, present state, and future direction of data at scale.  

Computers, of course, are key to solving this puzzle. 
We know that the real-time processing power of a single computer is limited - let's measure this by short-term memory capacity. 
This is true for everything from an ordinary laptop to a *bare metal* server we could rent from one of the cloud provider tech giants.
This is also something we can quantify:

<span style="font-weight: 400; padding-bottom: 20px;"> The RAM capacity of the average notebook typically falls between 8-16GB.</span>

As common sense also dictates, it would be inefficient to use such personal hardware for severely data-intensive tasks. What if we stick to a single hardware, but add some power to it?

<span style="font-weight: 400; padding-bottom: 20px;">The Macbook Pro with the <a href="https://support.apple.com/en-us/121553">Media Engine</a> has a maximum bandwidth of 546GB.</span>

This is an M4 Max chip specifically designed to boost memory performance. We're still well below Terrabyte scale. Google's data warehouse solution would consume this much data for about 2-3$. What if instead, we rented a single piece of hardware from them?

<span style="font-weight: 400; padding-bottom: 20px;">The most powerful Google Compute Engine, specifically memory-optimized, is the <a href="https://cloud.google.com/compute/docs/memory-optimized-machines">X4 machine series</a> with up to 32 TB of capacity.</span>


This is undoubtedly an impressive feat, but it also raises two further questions: Is it practical (and affordable)? What if we produce petabytes of data but don’t have access to a supercomputer to upgrade to?

The solution is straightforward, and there’s nothing particularly new here: we can pool multiple servers and harness their collective power. This is plain-old distributed computing. By allowing multiple physical computers (nodes) to work together in a cluster, we trust that they can solve our Big Problem.

Big Data, then, could be seen as any Analytics workflow repeatedly presenting us with problems, which we can only conceivably solve when pooling computing resources this way.
It is no surprise that to do this efficiently, we need to look for specialized tools in our artillery. It’s no trivial task to carry instructions over synchronous, yet otherwise disjointed, machines, telling them to safely access and manipulate our data. This brings us to the hype around <span style="font-weight: 400;">Apache Spark</span>.

## Why Spark is Industry Leading

Developed as an open-source project at UC Berkeley in 2009 and donated to the Apache foundation in 2013, Spark was specifically designed for this challenge.
Today, it is the most widely adopted open-source tool to work with data split across computers ("parallel"). It allows us to access and manipulate our datasets reliably, and recover information even if some individual computers collapse within our network ("fault tolerant").

In the public domain, Spark has no real credible competition, yet. 
[Hadoop](https://hadoop.apache.org/) deserves a mention as another Apache framework designed for distributed use cases, but it's slowly becoming a legacy solution. 
Whereas Spark processes data in memory, Hadoop consumes it in batches and works with external storage, leading to a significant performance overhead. 
On top of that, Spark has demonstrated versatility for other data domains, such as its powerful real-time [streaming engine](https://spark.apache.org/docs/latest/streaming-programming-guide.html). In terms of solving problems — both many and efficiently — Spark truly shines. 

<span style="font-weight: 400; padding-bottom: 20px;">How about the private domain?</span> 

Proprietary solutions are available, of course. Google's hosted data warehouse, BigQuery works under the hood exploiting the [Dremel](https://cloud.google.com/blog/products/data-analytics/new-blog-series-bigquery-explained-overview) query engine, well suited for distributed systems. Other hosted environments such as Snowflake will have a similar [proprietary alternative](https://0x0fff.com/snowflake-the-good-the-bad-and-the-ugly/) that does the work for them behind the scenes.
Spark itself is often deployed in hosted environments for easier setup and performance tuning.
The original authors went on to found the widely known analytics platform Databricks. 
It is one of the most reasonable options for hosting Spark, where they recently introduced an interesting performance improvement with the [Photon engine](https://www.databricks.com/product/photon). Let's come back to that later.

Databricks also integrates with the major cloud providers (AWS, GCP, Azure). In one form or another, the tech giants themselves have native solutions to work with Spark directly. In this category would be Google's Dataproc, Amazon EMR and Azure Synapse. 
All of these provide users with flexibility to fine-tune data processes based on context and business need. That serves as an alternative to subscribing to a hosted solution that may package some of its execution logic inside a black box (and potentially come with a higher price point).


## Why Spark Was Written in Scala

Let's take advantage of the fact that Spark is *not* one of such black boxes, and have a look inside.
Scala was the original language choice of the developers. Why does this matter? Let's try to understand the rationale behind that decision.

✅ First, Scala leverages the <span style="font-weight: 400;">power of the Java Virtual Machine (JVM)</span>, which is famed for its efficient, safe memory usage and optimized performance. So far, so good. 

✅ Second, Scala is a <span style="font-weight: 400;">type-safe language</span>. The program knows what to expect from each computing component, and safe execution is guaranteed.

If we were to stop here, there would be no shortage of alternatives: Java would equally qualify for the job. Why use Scala then, instead of its prevalent cousin? As a side note, Scala comes with great syntactic sugar, which spares us some development pain that Java won't address as kindly (Scala 3 is even braceless!). 
Assuming it’s not syntax but *functionality* to have justified the choice, Scala likely won the race for the following reasons:

✅ <span style="font-weight: 400;">Scala has lazy evaluation</span>. Computational resources are only deployed when they are first needed, making it a natural fit for Spark, where heavy reliance on efficient memory management is key. 

✅ Scala has <span style="font-weight: 400;">strong native support for functional programming</span>, which is naturally suited to a distributed setting. Common data operations like map, reduce, and filter are fundamental building blocks for Scala developers, making it an excellent choice for Big Data applications.

## Why Should We Care About This

<span style="font-weight: 400;">Python drastically lowers the entry barrier to using code to solve problems</span>.

This is especially true for analytics-related scripting, such as running a notebook to analyze an A/B test. The verdict is much the same for lower-level data engineering, too.
Companies, especially in tech, have increasingly come to realize this.
It is a sound business strategy to attract top talent from the statistical-data realm then train them to work with a Python ecosystem, which doesn't strictly require a Computer Science background. 

<span style="font-weight: 400;">Is this true for Big Data?</span>

With a Spark implementation in Python, analysts can write code autonomously in a language they are already familiar with, and start shuffling data on demand. 
This implementation, commonly seen in the industry, is <span style="font-weight: 400;">pySpark</span>. It serves as the wrapper layer between Python and the Spark API.

It's worth pausing here for a moment, though. Didn't we just argue that Scala was the optimal language choice for developing this technology in the first place? 
Python is typed dynamically (rather than statically), it's interpreted (rather than compiled), and its capacity for distributed computing is significantly reduced by something called the Global Interpreter Lock (GIL), which restricts execution to a single thread at a time. (For those outside the loop and curious about going down a rabbit hole, the GIL can be experimentally removed [Python 3.13 and upwards](https://docs.python.org/3/whatsnew/3.13.html). However, it is not yet close to becoming a stable feature of the language). 
 
All of this means that none of Python's inherent strengths are particularly suited to tackle the problem we originally set out to solve: working with high volume data over a distributed network. 
Sure enough, pandas or NumPy may work well on isolated machines, but they won’t function at all in a parallel environment.
Efficient memory management is not why Python is taking over the world, either — yet this is exactly what we need for Big Data processing.

<span style="font-weight: 400;">So, how is pySpark not only a legitimate, but vital industry tool?</span>

Beneath the service, the library works through a bridge (Py4J) and communicates directly with the JVM-based Spark core. 
It bypasses the standard Python execution model and attempts to move on to more familiar grounds as fast and simply as possible. 
This additional layer of processing doesn’t necessarily imply inferior performance, though. 
As long as we keep all data operations within the established JVM framework — by calling pySpark’s API functions — the performance difference should be negligible.
Problems start to occur when we run certain operations that force pure Python objects to be serialized and transferred to the JVM (the usual suspects here are UDFs). This serialization and deserialization process is a clear bottleneck specific to pySpark, and one that would be impossible to encounter in Scala, compiling and running natively on the JVM.


## Performance, Performance, Performance

<span style="font-weight: 400;">Where do we stand in the industry, then?</span>

Anecdotal evidence suggests that Scala execution can be up to 10x faster than Python. 
This might be true when we consider isolated code snippets in each language, but it isn’t a meaningful statement for our problem.
As we’ve seen, pySpark is just a guest in Python: our code will ideally execute the equivalent Spark API steps directly on the JVM.

Does science come to the rescue? An academic paper by [Ji & Kwon (2020)](https://koreascience.kr/article/JAKO202010163508830.page) suggests that Scala executes faster and is more scalable, but in the absence of the exact code they used in their case comparison, it’s difficult to determine whether Python-specific operations were introduced, requiring more serialization overhead than necessary.
Another paper by [Gupta & Kumari (2020)](https://ieeexplore.ieee.org/abstract/document/9452955) is, in fact, a step more cautious. 

To settle the debate for ourselves and form a conclusive opinion, we’re left with reading an entire book on Apache Spark Optimizations by [Karau & Warren (2017)](https://books.google.it/books?id=90glDwAAQBAJ&lpg=PP1&ots=FB7LR1Tjqg&dq=spark%20scala%20pySpark&lr&pg=PP1#v=onepage&q=spark%20scala%20pySpark&f=false). Alternatively, we can pick neatly organized bullet points from short articles on the subject — 
two of which are by [Intel](https://granulate.io/blog/pySpark-vs-spark-7-key-differences-how-to-choose/#Performance) and [MungingData](https://www.mungingdata.com/apache-spark/python-pyspark-scala-which-better/#performance-comparison). 

<span style="font-weight: 400;"> pySpark vs. Scala</span>

The consensus appears to be this. When used for simple tasks or when used wisely for complex tasks, pySpark gives us the ability to harness the full power of Spark. This is achieved at minimal or no additional cost and with the added benefit of Python’s easy-to-use programming modules.
However, unlike in Scala or other JVM-based languages, pySpark developers are prone to introducing unintentional performance bottlenecks if they don’t carefully consider how Spark code will be executed behind the scenes, from start to finish.


<span style="font-weight: 400;">Finally, we may not be far from third alternatives that will completely reset existing wisdom.</span> 

Databricks have developed the [<span style="font-weight: 400;">Photon engine</span>](https://www.databricks.com/product/photon), written entirely in C++. It integrates with Spark without the need for the JVM altogether. This is a pretty strong signal that they're betting on a significant performance boost and sustained commercial usage.
Possibly, then, the company founded by the original authors could write the next chapter in Big Data analytics, too.

Instead of opting for C++, others are placing their bet on the systems programming revolution that Rust might just bring about. A query engine written in Rust,
[<span style="font-weight: 400;">DataFusion</span>](https://news.apache.org/foundation/entry/apache-software-foundation-announces-new-top-level-project-apache-datafusion),
<span style="font-weight: 400;">was the top-level software project of Apache in 2024</span>.
It works in tandem with [<span style="font-weight: 400;">Arrow</span>](https://arrow.apache.org/), another tool suited to optimize storage and memory usage for analytics applications.
In fact, Apache now possesses an entire suite of Rust-based products (Arrow, Arrow Flight, Flight SQL, DataFusion, Ballista). In one way or another, they all have the potential to influence the Big Data realm. At the very least, it’s another sign that a breakthrough in distributed computing is just around the corner.

Another Rust-written tool, [<span style="font-weight: 400;">Polars</span>](https://pola.rs/) (or, as one redditor puts it, *pandas on steroids*), might raise the Big Data threshold — the point at which distributed computing tools become fundamentally necessary.

## Call It A Day

<span style="font-weight: 400;">Let's answer the clickbait and understand why your Big Data architecture might be flawed.</span>

According to Scala purists, if you’re not using Spark directly in its native environment, trouble is on the horizon. 
As of April 2025, Scala works most seamlessly with the existing JVM implementation of Spark.

According to the opposition, at least when used correctly, pySpark has proven to be a perfectly viable alternative. 
Moreover, the decision isn’t just technical: there are clear business costs involved in hiring Scala developers and maintaining data repositories that are inaccessible to most analysts and scientists at the company, who are extremely strong in their field but may only have intermediate programming knowledge. 

In the end, Scala stands as a performant, concise, and functional language, compelling developers to stay within the bounds of the intended optimal Big Data computing design. PySpark on the other hand, is the tool to have allowed extremely wide business applications for the technology of Spark. 
This shows again, that we're primarily faced with a *business* decision laden with trade-offs. Since both choices have their up- and downsides, it's better we resist the temptation to declare a definitive winner - there is not enough context to do so.
To make an already difficult dilemma worse, upcoming new technologies might steal the show, and do so sooner than we think.


### References

- Gupta, Y.K., & Kumari, S. (2020). *A Study of Big Data Analytics using Apache Spark with Python and Scala*. 3rd International Conference on Intelligent Sustainable Systems (ICISS).
- Ji, K., & Kwon, Y. (2020). *Performance comparison of Python and Scala APIs in Spark distributed cluster computing system*. Journal of Korea Multimedia Society. 
- Karau, H., & Warren, R. (2017). *High performance Spark: best practices for scaling and optimizing Apache Spark. " O'Reilly Media, Inc.".*
