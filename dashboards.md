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
