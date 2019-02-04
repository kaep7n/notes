# startup

## Serialize Enums as String by default

To serialize enumerations as string instead of a number the AddJsonOptions method can override the default behavoiur of Json.NET

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc().AddJsonOptions(options =>
    {
      options.SerializerSettings.Converters.Add(new Newtonsoft.Json.Converters.StringEnumConverter());
    });
}
```

also null values can be ignored by setting the NullValueHandling option

```csharp
options.SerializerSettings.NullValueHandling = Newtonsoft.Json.NullValueHandling.Ignore;
```



