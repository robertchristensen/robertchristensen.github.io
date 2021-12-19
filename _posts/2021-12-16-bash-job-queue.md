---
layout: post
title: "Bash job queue"
date: 2021-12-18 11:00:00 +0700
---

I have written a simple job queue system using Bash.  Sometimes I have
several programs I want to run.  Running all of them at once may overload
my system, because I run these on my laptop which is also used for other things.
It is convenient to submit several jobs, each one might vary slightly in arguments.
The jobs will run when the machine gets around to it, and the output is logged.

When this was written, I had the following goals:

* Jobs should queue.  Once a job has finished another should start.  Only a specific number of jobs should be running at a time.
* The system should be simple.
* The output of the batch job should be recorded and easily referenced.

These objectives were implemented in **bashJobQueue**.  The code can be found here [https://github.com/robertchristensen/bashJobQueue](https://github.com/robertchristensen/bashJobQueue).

The job queue is simple to use.  One reason for this is because the options
are limited.  Assuming all the programs are in the path, to submit
a job, run `submit` followed by what you want run.  For example
`submit python calculate_pi.py -n 10000` would run the program
`python` with the arguments `calculate_py.py -n 10000`.  Multiple
jobs can be queued.

When a job is submitted using the `submit`
command the environment is packaged as best it can so it can run
the program as if it was run when the job was submitted.  This is
done by recording the current working directory and all environment variables.  This is stored in a script.  When the
scheduler runs the program it restores the environment variables
and path the runs the script as provided in the `submit` command.
It does not save the script or files used.  This means the program or input data files used by the batched application should
not be modified.

To monitor the job status, the `status` command can be used.  Without arguments
this will list all jobs submitted and their current status.  If a job is
running or has run, `status 3` can be used to get the log for job 3.
For simplicity, both stdout and stderr is written to the same output.  When looking
at the logs for the job stdout and stderr are not differentiated.

When jobs are submitted they will be executed by the scheduler.  Jobs can be submitted even if the scheduler is not running.  It may be useful to queue many jobs
then start them running using the scheduler later.

The scheduler can be launched by using the `start_scheduler` command.  This command
has several arguments to configure how it starts.  The argument `-n k` indicates how many
parallel programs should be running at once.  This value can't be changed after the
scheduler starts.  `--queue-pending` will automatically queue jobs that have not started running.  Pending jobs might exist because the scheduler was not running when the job was submitted or if the scheduler was killed when the job was queued in the past.  Likewise, the `--queue-running` will automatically queue jobs that were
are in the running status.  Once a job starts running it will only be moved from the running status to finished status if it finishes.  If the job is not running but was terminated prematurely (such as if the scheduler was terminated) jobs might be stuck in the Running state even if they are not running.  These jobs can be restarted by using the `--queue-running` argument.  If this is done the output of
the job will be truncated when the job restarts.  An example of starting the scheduler is `start_scheduler -n 4 --queue-pending --queue-running`.  This will queue all jobs that have not finishes and will allow up to 4 jobs to run at the same time.

The job state can make some situations of the job scheduler a little strange.  With any tool, it is important to understand how it works and what it is doing.  Since
the scheduler is so simple, I decided it was okay to tolerate the strange behavior in exchange for a simpler implementation.

In future posts I plan to go through some specifics of how the scheduler was implemented.  The scheduler relies heavily on Bash and some basic tools available on most systems.

`start_scheduler -n 4 --queue-pending --queue-running
