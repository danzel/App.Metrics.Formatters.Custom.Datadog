Formatter for [App.Metrics](https://github.com/AppMetrics/AppMetrics) that formats output data as JSON compatible with the [Datadog](https://www.datadoghq.com/) API.

Usage:

```cs
var metrics = new MetricsBuilder()
    .Report.OverHttp(o =>
    {
        o.HttpSettings.RequestUri = new Uri("https://app.datadoghq.com/api/v1/series?api_key=" + apiKey);
        o.MetricsOutputFormatter = new DatadogFormatter(new DatadogFormatterOptions { Hostname = Environment.MachineName });
        o.FlushInterval = TimeSpan.FromSeconds(5);
    })
    .Build();
```