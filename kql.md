
### Performance Counter Distinct Names

```
Perf 
| where Computer == 'aks-agentpool-34378669-0'
| summarize by CounterValue(), CounterName
```
