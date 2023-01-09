# API Service

| Category     | SLI | SLO                                                                                                         |
|--------------|-----|-------------------------------------------------------------------------------------------------------------|
| Availability |   Total # of successful requests / Total # of requests  | 99%                                                                                                         |
| Latency      |   Buckets of requests in a histogram showing the 90th percentile over the last 1min   | 90% of requests below 100ms                                                                                 |
| Error Budget |  Error budget is defined at 20%. This means that 20% of the requests can fail and still be within the budget. It shows how much is left of your error budget (Remaining error budget in percentage = 1-[(1-compliance)/(1-objective)])	 |
| Throughput   |   Total # of successful requests over 1 seconds  | 5 RPS indicates the application is functioning                                                              |
