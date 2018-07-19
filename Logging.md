# Logging Best Practices

There are 6 types of logging levels as listed in the below table. The severity goes higher as we down the table.

| Log Level    | Purpose                                 | Use Case               |
| ------------ |:--------------------------------------| ----------------------|
| Trace        | It used to get whole response and request  | It's used only locally for debugging purposes |
| Debug        | It's used at in/out of the service | It's used in the services at the beginning and ending of the service. We can use params along with debug , so that we can know what parameters are used beginning and ending of the service |
| info         | It's used where we have huge service function that need to bookmark at paticular steps | Let's say we have orchestration function that talks to three different services then we can log info at start and end of each service consumption. |
| warn         | It's used where we know that error in other service will not affect our service. | Let's say we have a service which gives an expection and we know that this expection willn't affect our service then this can go to warn |
| error        | This is used to capture the expections that aren't aware of before | There could be an expections where we don't have any previous knowledge about it and there occurs during run time |
| server       | This is something that occur at down the line of the error hooks | |

# Logging Tools
* Winston - `https://github.com/winstonjs/winston` - Logging 
* Bunyan - `https://github.com/trentm/node-bunyan`

# Alerting Tools
* Airbrake - `https://airbrake.io/` - To  get emails and messges depend on serverity of logs

# Monitoring Tools
These are used to monitor the health of our services
* Datadog - `https://www.datadoghq.com/`
* Cloud watch - `https://aws.amazon.com/cloudwatch/` - AWS service
* Marathon - `https://mesosphere.github.io/marathon/` for Apache Mesos `https://mesos.apache.org/`

# Log Management Tools
These are used to collect and store logs
* Graylog - `https://www.graylog.org/`
* Splunk - `https://www.splunk.com/`

# Capture Application tools
* New relic - `https://newrelic.com/` - captures app metrices such as memory leaks, each service run time, cpu consumption

# Dynamic logging
This is something where the log levels are changed dynamically. Let's a say we have an secure endpoint which the user hits it we change the log.info to log.debug. It's recommend at very cost and should be careful in implementing. Sometimes few instances will not able to change themseleves.
We can implement this through SNS as where we notify our services and they change their log levels depending on the notification.