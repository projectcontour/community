The cloud native ecosystem is moving rapidly - ingress controllers and their feature sets are no exception.
We've made our best effort to survey the ingress controller landscape and compare to our core feature set.

If you find something outdated or outright erroneous, please submit a PR and we'll fix it right away.

Table updated on 3/6/2020 against Contour 1.2.1

✓✗
| Feature                                                | Contour                                  | NGINX Ingress Controller         | Traefik                               | Istio Ingress                            | Ambassador                                 |
| -------------:                                         | :-------------------------------------:  | :------------------------------: | :-----------------------------------: | :--------------------------------------: | :----------------------------------------: |
| License                                                | Apache 2.0                               | Apache 2.0                       | MIT                                   | Apache 2.0                               | Apache 2.0                                 |
| Protocol Support                                       | L7, L4 via SNI                           | L7, L4, UDP                      | L7, L4, UDP                           | L7, L4                                   | L7, L4                                     |
| TCP SSL Passthrough                                    | ✓                                        | ✓                                | ✗                                     | ✓                                        | ✓                                          |
| Authentication                                         | ✗                                        | Basic, Client Certificate, OAuth | Basic                                 | JWT                                      | Basic, OAuth                               |
| Traffic Distribution                                   | RoundRobin, WeightedLeastRequest, Random | EWMA, RoundRobin                 | RoundRobin                            | RoundRobin, WeightedLeastRequest, Random | RoundRobin, LeastRequest, RingHash, Maglev |
| Observability (logging, metrics, etc)                  | Prometheus                               | Prometheus                       | DataDog, InfluxDB, Prometheus, StatsD | Prometheus                               | Prometheus, StatsD                         | 
| SSL Termination                                        | ✓                                        | ✓                                | ✓                                     | ✓                                        | ✓                                          | 
