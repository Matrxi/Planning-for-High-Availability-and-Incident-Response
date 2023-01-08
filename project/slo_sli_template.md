# API Service

| Category     | SLI | SLO                                                                                                         |
|--------------|-----|-------------------------------------------------------------------------------------------------------------|
| Availability |   Total # of successful requests / Total # of requests  | 99%                                                                                                         |
| Latency      |   Buckets of requests in a histogram showing the 90th percentile over the last 1min   | 90% of requests below 100ms                                                                                 |
| Error Budget |   1 – (# of successful requests/# of total requests)  | Error budget is defined at 20%. This means that 20% of the requests can fail and still be within the budget |
| Throughput   |   Total # of successful requests over 1 seconds  | 5 RPS indicates the application is functioning                                                              |
