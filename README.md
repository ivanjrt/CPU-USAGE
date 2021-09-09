# CPU-USAGE
``` JavaScript
Get-Counter '\Process(*)\% Processor Time' `
    | Select -ExpandProperty countersamples `
    | Select -Property instancename, cookedvalue `
    | Sort -Property cookedvalue -Descending `
    | Select -First 10 `
    | ft InstanceName,@{L='CPU';E={($_.Cookedvalue/100).toString('P')}} -AutoSize -ErrorAction SilentlyContinue
```
WIP: create an Ojbect and find out why it throws an exception and a RAM Monitor <br/>

I have this for RAM <br/>
```(Get-Counter '\Memory\Available MBytes').CounterSamples.CookedValue```

source Idea: <a href="https://stackoverflow.com/questions/6298941/how-do-i-find-the-cpu-and-ram-usage-using-powershell">link text</a>
