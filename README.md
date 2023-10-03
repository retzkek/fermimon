# FermiMon

Fermilab is one of the world's premier high-energy physics lab and the computing
needs to keep exploring the frontiers of physics is growing exponentially,
stretching the lab's goverment-allocated budget. In the interest of making the
best use of the taxpayers' money, you've been tasked with helping improve the
efficiency of the batch jobs that the physicists are running, to better utilize
the computing resources we already have.

The sys admin group has set up a process to monitor the resource usage by the
jobs, which yields a plain text file every day that contains, for each job that
ran:

* the *job ID*
* the *experiment* that owns the job
* the *host* on which the job ran
* the *maximum memory* that was requested and allocated for the job in MiB
* the *timestamp* of when the job started running
* a *time series* of data, that contains:
  * the *timestamp* when the data was taken
  * the *CPU usage* as a fraction of one core
  * the *memory usage* in MiB
  
See the example input data below.

## Requirements

To better understand the scale of the problem (if there is indeed one), you've
decided to print a report from each day's data that summarizes each job's
efficiency.

The ideal job fully utilizes the CPU, and uses close to the requested memory as
possible. As a first pass though, you just want to identify jobs and experiments
that are below **75%** CPU utilization efficiency and **80%** requested memory
efficiency.

For each job in the input data print the job ID and whether the job was above
both efficiencies ("OK"), below CPU efficiency ("CPU"), below memory efficiency
("MEM"), or both ("MC").

See the example output below.

* Your solution should read the input from stdin and write the output to stdout.
* Use whatever language, libararies, or tools you like (and can justify), so long
  as they are commonly available.
* Share your source and a document (which can be comments in the source file(s)) with
  any requirements and instructions to build and run.
* Your solution should follow the examples but as a valued contributor and
  stakeholder, feel free to propose any improvments you'd make (for example: in
  data format, analysis methods, or criteria).


## Example Input

    job: 123.0 mu2e pc01.fnal.gov 1024.0 2023-04-01T01:00:00Z
    2023-04-01T01:00:30Z 0.82 868.0
    2023-04-01T01:01:00Z 0.87 974.3
    2023-04-01T01:01:30Z 0.78 1248.1
    job: 124.0 dune pc02.fnal.gov 2048.0 2023-04-01T02:38:00Z
    2023-04-01T02:38:01Z 0.23 120.8
    2023-04-01T02:38:31Z 0.36 596.0
    2023-04-01T02:39:02Z 0.82 1854.3
    job: 124.1 nova pc01.fnal.gov 1024.0 2023-04-01T03:20:00Z
    2023-04-01T06:00:01Z 0.61 718.0
    2023-04-01T06:00:31Z 0.99 896.8
    2023-04-01T06:01:02Z 0.95 932.5

### Description 

This example presents the data for three jobs. The first job has the following
information:

* job ID: 123.0
* experiment: mu2e
* host: pc01.fnal.gov
* requested memory: 1024.0 MiB
* starting time: April 1, 2023 1:00:00 AM UTC

There is then observed data from three timestamps. The first data point shows
the job used 82% of CPU and 868 MiB of memory at 1:00:30 AM UTC.

## Example Output

    123.0 OK
    124.0 CPU
    124.1 MC
