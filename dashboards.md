# service summary
![Dashboard](images/version1.png)
 ```{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    )`
  ],
  name: "Servlet Request Hits",
  unit: "hits",
  type: "bar",
  description: "Total number of servlet requests handled by the recommendationservice server spans in the dev environment. This metric represents incoming request volume aggregated over time."
}
```
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    )`
  ],
  name: "Servlet Request Errors",
  unit: "errors",
  type: "bar",
  description: "Total number of servlet requests that resulted in errors for the recommendationservice server spans in the dev environment. This metric helps identify failed or unhealthy requests."
}
```
![Dashboard](images/version2.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ).as_rate()`
  ],
  name: "Servlet Request Hit Rate",
  unit: "hits/s",
  type: "Lineplot",
  description: "Rate of incoming servlet requests per second for the recommendationservice server spans in the dev environment. This metric shows real-time traffic intensity rather than total request volume."
}
```
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ).as_rate()`
  ],
  name: "Servlet Request Error Rate",
  unit: "errors/s",
  type: "Lineplot",
  description: "Rate of failed servlet requests per second for the recommendationservice server spans in the dev environment. This metric helps identify periods of elevated failure frequency."
}
```
![Dashboard](images/version3.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Hits by Version",
  unit: "hits",
  type: "bar",
  description: "Bar chart showing the total number of servlet requests handled by each deployed version of the recommendationservice in the dev environment. This visualization helps compare traffic distribution across service versions during deployments or rollouts."
}
```
![Dashboard](images/version4.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    ).as_rate()`
  ],
  name: "Servlet Request Hit Rate by Version",
  unit: "hits/s",
  type: "Area",
  description: "Area chart showing the per-second rate of servlet requests handled by each deployed version of the recommendationservice in the dev environment. This visualization helps analyze traffic distribution and rollout behavior across service versions over time."
}
```
![Dashboard](images/version5.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {http.status_code}
    )`
  ],
  name: "Servlet Request Errors by HTTP Status Code",
  unit: "errors",
  type: "bar",
  description: "Bar chart showing the total number of servlet request errors grouped by HTTP status code for the recommendationservice in the dev environment. This visualization helps identify the dominant error classes, such as 5xx server-side failures."
}
```
![Dashboard](images/version6.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {http.status_code}
    ).as_rate()`
  ],
  name: "Servlet Request Error Rate by HTTP Status Code",
  unit: "errors/s",
  type: "Area",
  description: "Area chart showing the per-second rate of servlet request errors grouped by HTTP status code for the recommendationservice in the dev environment. This visualization highlights the frequency and trend of server-side failures over time."
}
```
![Dashboard](images/version7.png)
```
{
  expr: [
    `(
      sum(
        trace:servlet:request:errors{
          env:dev,
          service:recommendationservice,
          span.kind:server
        } by {http.status_code}
      ).as_rate()
      /
      sum(
        trace:servlet:request:hits{
          env:dev,
          service:recommendationservice,
          span.kind:server
        }
      ).as_rate()
    )`
  ],
  name: "Servlet Request Error Rate",
  unit: "percent",
  type: "Lineplot",
  description: "Line plot showing the error rate (percentage of failed requests) for the recommendationservice in the dev environment. The error rate is calculated as the ratio of servlet request errors per second to total servlet request hits per second, highlighting periods of complete or partial service failure."
}
```
![Dashboard](images/version8.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Errors by Version",
  unit: "errors",
  type: "bar",
  description: "Bar chart showing the total number of servlet request errors grouped by service version for the recommendationservice in the dev environment. This visualization helps identify faulty deployments by comparing error volume across different service versions."
}
```
![Dashboard](images/version9.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:errors{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    ).as_rate()`
  ],
  name: "Servlet Request Error Rate by Version",
  unit: "errors/s",
  type: "Area",
  description: "Area chart showing the per-second rate of servlet request errors grouped by service version for the recommendationservice in the dev environment. This visualization helps identify which deployment versions are actively generating failures over time."
}
```
![Dashboard](images/version10.png)
```
{
  expr: [
    `(
      sum(
        trace:servlet:request:errors{
          env:dev,
          service:recommendationservice,
          span.kind:server
        } by {version}
      ).as_rate()
      /
      sum(
        trace:servlet:request:hits{
          env:dev,
          service:recommendationservice,
          span.kind:server
        } by {version}
      ).as_rate()
    )`
  ],
  name: "Servlet Request Error Rate by Version",
  unit: "percent",
  type: "Lineplot",
  description: "Line plot showing the error rate percentage per service version for the recommendationservice in the dev environment. The metric is calculated as the ratio of servlet request errors per second to total servlet request hits per second, clearly highlighting faulty deployments where nearly all traffic fails."
}
```
![Dashboard](images/verssion11.png)
```
{
  expr: [
    `p50(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p50) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "Line plot showing the p50 (median) servlet request latency grouped by service version for the recommendationservice in the dev environment. This visualization helps compare typical response time behavior across different deployments."
}
```
![Dashboard](images/version12.png)
```
{
  expr: [
    `p50(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p50) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p50) servlet request latency grouped by error flag for the recommendationservice in the dev environment. Compares latency behavior of successful (error=false) and failed (error=true) requests."
}
```
![Dashboard](images/version13.png)
```
{
  expr: [
    `avg(
      trace:servlet:request.apdex{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    )`
  ],
  name: "Servlet Request Apdex",
  unit: "",
  type: "Lineplot",
  description: "Apdex score for servlet requests on the recommendationservice in the dev environment. Apdex represents overall user satisfaction based on request latency and errors, with values ranging from 0 (poor) to 1 (excellent)."
}
```
![Dashboard](images/version14.png)
```
{
  expr: [
    `p75(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p75) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "p75 servlet request latency grouped by service version for the recommendationservice in the dev environment. This graph compares how the upper-quartile latency (75% of requests complete faster than this value) behaves across different deployments."
}
```
![Dashboard](images/version15.png)
```
{
  expr: [
    `p75(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p75) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "p75 servlet request latency grouped by error flag for the recommendationservice in the dev environment. Compares upper-quartile latency between successful (error=false) and failed (error=true) requests to understand failure behavior."
}
```
![Dashboard](images/version16.png)
```
{
  expr: [
    `avg(
      trace:servlet:request.apdex{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    )`
  ],
  name: "Apdex Score",
  unit: "",
  type: "Lineplot",
  description: "Average Apdex score for servlet requests on the recommendationservice in the dev environment. Apdex ranges from 0 to 1 and reflects overall user satisfaction based on request latency and error behavior."
}
```
![Dashboard](images/version17.png)
```
{
  expr: [
    `p90(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p90) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "p90 servlet request latency grouped by service version for the recommendationservice in the dev environment. Highlights tail latency behavior and helps identify performance regressions across deployments."
}
```
![Dashboard](images/version18.png)
```
{
  expr: [
    `p90(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p90) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "p90 servlet request latency split by error status for the recommendationservice in the dev environment. Highlights whether tail latency is driven by failed or successful requests."
}
```
![Dashboard](images/version19.png)

```
{
  expr: [
    `p95(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p95) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "p95 servlet request latency grouped by service version for the recommendationservice in the dev environment. Highlights extreme tail latency and helps identify performance regressions affecting the slowest requests across deployments."
}
```
![Dashboard](images/version20.png)
```
{
  expr: [
    `p95(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p95) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "p95 servlet request latency split by error status (true vs false) for the recommendationservice in the dev environment. Helps determine whether extreme tail latency is driven by failed requests or slow successful execution paths."
}
```
![Dashboard](images/version21.png)
```
{
  expr: [
    `p99(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p99) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "p99 servlet request latency grouped by service version for the recommendationservice in the dev environment. Highlights extreme tail latency affecting the slowest 1% of requests and helps identify severe performance regressions or improvements across deployments."
}
```
![Dashboard](images/version22.png)
```
{
  expr: [
    `p99(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p99) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "Line plot showing the p99 (99th percentile) servlet request latency split by error status (true vs false) for the recommendationservice in the dev environment. This helps determine whether tail latency is primarily caused by failed requests or by slow successful requests."
}
```
![Dashboard](images/version23.png)
```
{
  expr: [
    `p99.9(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Latency (p99.9) by Version",
  unit: "ms",
  type: "Lineplot",
  description: "Line plot showing the p99.9 (99.9th percentile) servlet request latency grouped by service version for the recommendationservice in the dev environment. This graph highlights extreme tail latency and helps identify whether specific deployments introduce severe outliers affecting a very small percentage of requests."
}
```
![Dashboard](images/version24.png)
```
{
  expr: [
    `p99.9(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {error}
    )`
  ],
  name: "Servlet Request Latency (p99.9) by Error",
  unit: "ms",
  type: "Lineplot",
  description: "Line plot showing the p99.9 (99.9th percentile) servlet request latency split by error status (true vs false) for the recommendationservice in the dev environment. This visualization highlights extreme tail latency and helps identify whether the worst latency spikes are associated with failed requests or successful ones."
}
```
![Dashboard](images/version25.png)
```
{
  expr: [
    `max(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {version}
    )`
  ],
  name: "Servlet Request Max Latency by Version",
  unit: "s",
  type: "Lineplot",
  description: "Line plot showing the maximum observed servlet request latency grouped by service version for the recommendationservice in the dev environment. This graph highlights worst-case latency spikes per deployment version and helps identify versions that introduce severe performance regressions or outliers."
}
```
# endpoints
![Dashboard](images/version26.png)
```
{
  expr: [
    `top(
      sum:trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {resource_name},
      5,
      'mean',
      'desc'
    )`
  ],
  name: "Top Servlet Endpoints by Request Volume",
  unit: "hits",
  type: "Bar",
  description: "Bar chart showing the top 5 servlet request endpoints by total request count, grouped by resource_name, for the recommendationservice in the dev environment. This visualization highlights the most frequently accessed endpoints and helps identify traffic hotspots and dominant API routes."
}
```
![Dashboard](images/version27.png)
```
{
  expr: [
    `top(
      sum:trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      } by {resource_name},
      10,
      'mean',
      'desc'
    )`
  ],
  name: "Top 10 Servlet Endpoints by Request Volume",
  unit: "hits",
  type: "Bar",
  description: "Bar chart displaying the top 10 servlet endpoints ranked by average request volume, grouped by resource_name, for the recommendationservice in the dev environment. This graph helps identify the most frequently accessed APIs and understand traffic distribution across endpoints."
}
```
![Dashboard](images/version28.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Servlet Request Hits by Endpoint",
  unit: "hits",
  type: "Bar",
  description: "Bar chart showing the total number of servlet requests grouped by resource_name for the recommendationservice in the dev environment. This visualization provides a complete view of traffic distribution across all endpoints without limiting to top-N results."
}
```
![Dashboard](images/version29.png)
```
{
  expr: [
    `top(
      sum(
        trace:servlet:request:hits{
          env:dev,
          service:recommendationservice,
          span.kind:server
        }
      ) by {resource_name}.as_rate(),
      5,
      'mean',
      'desc'
    )`
  ],
  name: "Top 5 Endpoint Request Rate (hits/sec)",
  unit: "hits/s",
  type: "Lineplot",
  description: "Line plot showing the request rate (hits per second) for the top 5 servlet endpoints, grouped by resource_name and ranked by mean traffic, for recommendationservice in the dev environment. This visualization helps identify the most actively used endpoints over time."
}
```
![Dashboard](images/version30.png)
```
{
  expr: [
    `top(
      sum(
        trace:servlet:request:hits{
          env:dev,
          service:recommendationservice,
          span.kind:server
        }
      ) by {resource_name}.as_rate(),
      10,
      'mean',
      'desc'
    )`
  ],
  name: "Top 10 Endpoint Request Rate (hits/sec)",
  unit: "hits/s",
  type: "Lineplot",
  description: "Line plot showing the request rate (hits per second) for the top 10 servlet endpoints, grouped by resource_name and ranked by mean traffic, for recommendationservice in the dev environment. This helps identify the most frequently accessed endpoints and observe traffic trends over time."
}
```
![Dashboard](images/version31.png)
```
{
  expr: [
    `sum(
      trace:servlet:request:hits{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}.as_rate()`
  ],
  name: "Request Rate by Endpoint",
  unit: "hits/s",
  type: "Lineplot",
  description: "Request rate (hits per second) for each servlet endpoint, grouped by resource_name, for recommendationservice in the dev environment. This shows traffic patterns and load distribution across endpoints over time."
}
```
![Dashboard](images/version32.png)
```
{
  expr: [
    `avg(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Average Servlet Request Latency by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Average servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify endpoints with higher average response times."
}
```
```
{
  expr: [
    `p50(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p50) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p50) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `p75(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p75) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p75) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `p90(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p90) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p90) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `p95(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p95) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p95) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `p99(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p99) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p99) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `p99.9(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (p99.9) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (p99.9) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
```
{
  expr: [
    `max(
      trace:servlet:request{
        env:dev,
        service:recommendationservice,
        span.kind:server
      }
    ) by {resource_name}`
  ],
  name: "Median Servlet Request Latency (max) by Endpoint",
  unit: "ms",
  type: "Lineplot",
  description: "Median (max) servlet request latency grouped by resource_name (endpoint) for the recommendationservice in the dev environment. Displays the top 5 endpoints ranked by mean latency, helping identify which endpoints typically respond slower under normal conditions."
}
```
