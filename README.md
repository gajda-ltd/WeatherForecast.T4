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
    public sealed record WeatherForecast
    {
    }
}
```
