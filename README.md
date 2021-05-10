```
TextTemplatingFileGenerator
```

```
<#@ template  debug="true" hostSpecific="true" #>
<#@ output extension=".cs" #>
<#@ Assembly Name="System.Core" #>
<#@ Assembly Name="System.Windows.Forms" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System" #>
<#@ import namespace="System.IO" #>
<#@ import namespace="System.Diagnostics" #>
<#@ import namespace="System.Linq" #>
<#@ import namespace="System.Collections" #>
<#@ import namespace="System.Collections.Generic" #><#
    var hostServiceProvider = (IServiceProvider)this.Host;
    var directory = Path.GetDirectoryName(this.Host.TemplateFile);
    var currentDirectory = directory.Substring(directory.LastIndexOf("\\") + 1);
    var dte = (DTE)hostServiceProvider.GetService(typeof(DTE));    
    var projectItem = dte.Solution.FindProjectItem(Host.TemplateFile);
    var project = projectItem.ContainingProject;
    var nameSpace = project.Name + "." + currentDirectory;
#>namespace <#= nameSpace #>
{
    using System;

    public sealed record WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureC { get; set; }
        public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
        public string Summary { get; set; }
    }
}
```

https://www.bing.com/th?id=OHR.Hokulea_EN-US8698576653_UHD.jpg
