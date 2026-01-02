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
