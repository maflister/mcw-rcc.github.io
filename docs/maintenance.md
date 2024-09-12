# Maintenance

Research Computing uses scheduled maintenance windows to perform upgrades and general upkeep of all systems. Maintenance occurs every first Wednesday of the month from 9PM-12AM.

## 2024 Schedule

- January 3, 2024
- February 7, 2024
- March 6, 2024
- April 3, 2024
- May 1, 2024
- June 5, 2024
- July 3, 2024
- August 7, 2024
- September 4, 2024
- October 2, 2024
- November 6, 2024
- December 4, 2024

## Job scheduling around maintenance

If you submit a job before a maintenance window and the job is sitting in the queue, first check to see why with `squeue`. In the output, you'll see the last column `NODELIST(REASON)`. If your job is held for maintenance, you'll see `(ReqNodeNotAvail, Reserved for maintenance)`.

Each job has a [walltime request](user-guide/jobs/running-jobs.md#time). The walltime request sets the amount of time that your job will be allowed to run on the cluster. On the HPC cluster, the maximum allowed walltime is 7 days.

If you submit your job with X hours walltime request, and the maintenance window starts in less than X hours, the job will be held until after the maintenance window closes. The reason is that the scheduler cannot guarantee your job will finish before maintenance begins.

To make the job run, resubmit your job with a walltime request that ensures the job will finish before the maintenance window. We can use a simple formula to find that walltime.

`walltime = ( $maint_start_time - $current_time )`

To simplify the process, use the `maxwalltime` command, which provides the maximum walltime request that will also allow your job to run before maintenance.
