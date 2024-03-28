+++
title="The devops page"
date=2024-03-10
[taxonomies]
tags=["the-page"]
+++

What to do when launching your first deployment of anything.

# Data and metrics

Decision makers need to provide usage information to help run a system.
This is not system metrics, but rather[^Siebenmann]

- how much things are being used
- who is using them
- why are they using them

Therefore, a dashboard is always a good idea.
Internal services are not automatically instrumented to gather this sort of usage information.
Therefore, you will want to hunt around for creative ways to generate this data from low-level metrics and logs.

Always:

- write down how you generated that usage information
- rationale for doing it this way

such that all data is reproducible.

Secondly, make sure to see if there is data you can easily collect and retain to provide better usage information in the future.
End of session summary log records are great: a log record that puts all the information about a **user session** in a single place.

Finally, note that one of the key ideas is to collect metrics to assess how responsive systems are when people are trying to do things on them.

> Of course there are privacy implications of retaining lots of logs and usage data.
> This may be a good time to ask around to get advance agreement on what sort of usage information you want to be able to provide and what sort you definitely don't want to have available for people to ask for.
> This is also another use for arranging to log your own 'end of session' summary records, because if you're doing it yourself you can arrange to include only the usage information you've decided is okay.[^Siebenmann]


## Disk IO and runqueue latency graphs

> For a long time I've been collecting disk IO latency histograms, and recently I've been collecting runqueue latency histograms (using the eBPF exporter and a modified version of libbpf/tools/runqlat.bpf.c). This has caused me to think about the various sorts of latency that affects responsiveness and how I can measure it.[^Siebenmann1]

Run queue latency is the latency between when a task becomes able to run (or when it got preempted in the middle of running) and when it does run. 
This latency is effectively the minimum (lack of) response from the system and is primarily affected by CPU contention, since the major reason tasks have to wait to run is other tasks using the CPU.
For obvious reasons, high(er) run queue latency is related to CPU pressure stalls, but a histogram can show you more information than an aggregate number. 
I expect run queue latency to be what matters most for a lot of programs that mostly talk to things over some network (including talking to other programs on the same machine), and perhaps some of their time burning CPU furiously.
If your web browser can't get its rendering process running promptly after the HTML comes in, or if it gets preempted while running all of that Javascript, this will show up in run queue latency.
The same is true for your window manager, which is probably not doing much IO.

Disk IO latency is the lowest level indicator of things having to wait on IO; it sets a lower bound on how little latency processes doing IO can have (assuming that they do actual disk IO).
However, direct disk IO is only one level of the Linux IO system, and the Linux IO system sits underneath filesystems.
What actually matters for responsiveness and latency is generally how long user-level filesystem operations take.
In an environment with sophisticated, multi-level filesystems that have complex internal behavior (such as ZFS and its ZIL), the actual disk IO time may only be a small portion of the user-level timing, especially for things like fsync().

(Some user-level operations may also not do any disk IO at all before they return from the kernel (for example).
A read() might be satisfied from the kernel's caches, and a write() might simply copy the data into the kernel and schedule disk IO later.
This is where histograms and related measurements become much more useful than averages.)

Measuring user level filesystem latency can be done through eBPF, to at least some degree; libbpf-tools/vfsstat.bpf.c hooks a number of kernel vfs_* functions in order to just count them, and you could convert this into some sort of histogram. 
Doing this on a 'per filesystem mount' basis is probably going to be rather harder.
On the positive side for us, hooking the vfs_* functions does cover the activity a NFS server does for NFS clients as well as truly local user level activity. 
Because there are a number of systems where we really do care about the latency that people experience and want to monitor it, I'll probably build some kind of vfs operation latency histogram eBPF exporter program, although most likely only for selected VFS operations (since there are a lot of them).

I think that the straightforward way of measuring user level IO latency (by tracking the time between entering and exiting a top level vfs_* function) will wind up including run queue latency as well.
You will get, basically, the time it takes to prepare and submit the IO inside the kernel, the time spent waiting for it, and then after the IO completes the time the task spends waiting inside the kernel before it's able to run.

Because of how Linux defines iowait, the higher your iowait numbers are, the lower the run queue latency portion of the total time will be, because iowait only happens on idle CPUs and idle CPUs are immediately available to run tasks when their IO completes.
You may want to look at io pressure stall information for a more accurate track of when things are blocked on IO.

A complication of measuring user level IO latency is that not all user visible IO happens through read() and write().
Some of it happens through accessing mmap()'d objects, and under memory pressure some of it will be in the kernel paging things back in from wherever they wound up.
I don't know if there's any particularly easy way to hook into this activity.

# References

[^DevaultSourceHut]: Drew Devault, _SourceHut network outage post-mortem_, Published 2024-01-19, [[Online]](https://sourcehut.org/blog/2024-01-19-outage-post-mortem/)

[^Paterson]: Cal Paterson, _S3 is files, but not a filesystem_, Published 2024-03, [[Online]](https://calpaterson.com/s3.html)

[^Siebenmann]: Chris Siebenmann, _Some thoughts on usage data for your systems and services_, Published 2024-03-09, [[Online]](https://utcc.utoronto.ca/~cks/space/blog/sysadmin/UsageDataSomeBits)

[^Siebenmann1]: ..., _Scheduling latency, IO latency, and their role in Linux responsiveness_, Published 2024-03-10, [[Online]](https://utcc.utoronto.ca/~cks/space/blog/linux/SystemResponseLatencyMetrics)

[^Siebenmann2]: ..., _Everything that does TLS should log the SSL parameters used_, Published 2024-03-13, [[Online]](https://utcc.utoronto.ca/~cks/space/blog/sysadmin/SSLLogConnectionInfo)

https://utcc.utoronto.ca/~cks/space/blog/sysadmin/UsageDataWhyCare
