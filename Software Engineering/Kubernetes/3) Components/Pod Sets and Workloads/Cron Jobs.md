[Documentation](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/)
A cron (chronological) job is a job that runs on some kind of schedule or calendar such as report generation or backups. They are normally given in Cron format, which is required due to the nature of the job.
# Create a Cron Job
## Cron Format
Cron formats are five fields separated with a space, and is used to define a time of day in which to run, not a time interval between runs. The numbers increase from left to right with minute, hour, day of month, month, and day of week (0-7 (0 and 7 are both Sunday)). Note granularity is only to the minute

| Field            | Description                           | Allowed Values                                  |
| ---------------- | ------------------------------------- | ----------------------------------------------- |
| **Minute**       | The minute of the hour.               | 0–59                                            |
| **Hour**         | The hour of the day (24-hour format). | 0–23                                            |
| **Day of Month** | The day of the month.                 | 1–31                                            |
| **Month**        | The month of the year.                | 1–12 (or JAN–DEC)                               |
| **Day of Week**  | The day of the week.                  | 0–6 (or SUN–SAT, where 0 and 7 are both Sunday) |
### Special Characters

### Predefined Schedules


## Examples
Here are some examples and their schema, again remember "\*" matches "any match"

| **Schema**     | **Function**                               |
| -------------- | ------------------------------------------ |
| 5 0 \* \* \*   | "Run 5 minutes after midnight every day"   |
| 15 14 1 \* \*  | "Run at 14:15 on the first of every month" |
| 0 22 \* \* 1-5 | "Run monday to friday, at 22:00"           |
| 5 4 \* \* sun  | "run at 04:05 on sundays"                  |
