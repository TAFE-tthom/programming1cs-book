# Server-side Rendering and ASP.NET



* HTTP method - A method is part of the `HTTP` protocol, it is used to outline the kind of request you are performing. Common HTTP Methods are: GET, POST, PUT, DELETE.

* Port - A port, is a virtual port or application port, when a server is running (your express application), it needs to listen on a port for incoming connections. This allows the operating system to direct network traffic to the application.

* endpoint - An endpoint is typically a `HTTP` URL, similar to what you put into the browser.

* controller - A class, type or component which represents handling domain logic (like processing a payment or cancelling an order). These controllers can have more than one method associated with them. In the perspective of a WebAPI, they will have different http methods associated.

* `app` - This is a common variable inside express applications that will usually have a `dictionary` that holds onto different response callbacks as well as other objects and services.


## Making your own WebAPI

Within the C# ecosystem, it is common to use **ASP.NET** as a framework to build a webapi. This will provide a solid development server and structure for constructing controller and endpoints. To get started, you will need to use the `webapi` template.

```
dotnet new webapi --use-controllers
```

By specifying the `--use-controllers` flag here, we are able to construct some sensible default files. By doing this, you will have the following files generated.

```
appsettings.Development.json  aspdemo.csproj  bin          obj         Properties
appsettings.json              aspdemo.http    Controllers  Program.cs  WeatherForecast.cs
```

It will be using Microsoft's `WeatherForecast` template here which will demonstrate the interaction between the **Model** types and the **Controller** types. `WeatherForecast.cs` file will contain a simple class with properties or simple conversion function.

```cs 
public class WeatherForecast
{
    public DateOnly Date { get; set; }

    public int TemperatureC { get; set; }

    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);

    public string? Summary { get; set; }
}
```

### Controller Methods

Within the `Controllers/WeatherForecastController.cs` file, we can observe the following HTTP `GET` method which will return an array of `WeatherForecast` objects.


```cs
[HttpGet(Name = "GetWeatherForecast")]
public IEnumerable<WeatherForecast> Get()
{
    return Enumerable.Range(1, 5).Select(index => new WeatherForecast
    {
        Date = DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
        TemperatureC = Random.Shared.Next(-20, 55),
        Summary = Summaries[Random.Shared.Next(Summaries.Length)]
    })
    .ToArray();
}
```

The `Range` method associated with `Enumerable` will generate 5 items of which, for each item, we will create a new `WeatherForecast` object with each field initialised specifically.

When this endpoint is hit, it will return an array to the frontend in the form of a JSON object.

```json
[
  {"date":"2026-01-28","temperatureC":-9,"temperatureF":16,"summary":"Scorching"},
  {"date":"2026-01-29","temperatureC":1,"temperatureF":33,"summary":"Scorching"},
  {"date":"2026-01-30","temperatureC":6,"temperatureF":42,"summary":"Hot"},
  {"date":"2026-01-31","temperatureC":2,"temperatureF":35,"summary":"Warm"},
  {"date":"2026-02-01","temperatureC":50,"temperatureF":121,"summary":"Sweltering"}
]
```

The above array is returned to the frontend and we can see the relevant properties of the C# class being converted to an appropriate field as a JSON object. There is an automatic serialisation process going on on the return statement.

You can test this by visiting `http://localhost:5062/weatherforecast` in the browser or by using a command with curl. `curl localhost:5062/weatherforecast`.


Within a HTTP `POST` method, we will make a simple POST that will operate like the `GET` method.

```cs

[HttpPost(Name = "PostWeatherForecast")]
public IEnummerable<WeatherForecast> Post()
{

  return Enumerable.Range(1, 5).Select(index => new WeatherForecast
  {
      Date = DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
      TemperatureC = Random.Shared.Next(-20, 55),
      Summary = Summaries[Random.Shared.Next(Summaries.Length)]
  })
  .ToArray();
}
```

To test this with curl, you can use the following command.

```
curl -XPOST localhost:5062/weatherforecast
```

The above will specify the `POST` http method and request the data like so. We can construct a different method instead of using `IEnummerable` return type or just generating weather forecast objects.

Let's now create a new `WeatherForecast` object using information from the `Body` of a http request. We will introduce an attribute called `FromBody` which, given this attribute will attempt to **deserialize** the data before it hits the function.

```cs
[HttpPost(Name = "PostWeatherForecast")]
public WeatherForecast Post([FromBody] WeatherForecast forecast)
{
  return forecast;
}
```

The above snippet will accept the data given to it, transform it into a C# object and return it back to the sender. If we can achieve this, then we can change the function to write to a database or file.

To test your method, you can use the following script.

```
curl -XPOST -H "Content-Type: application/json" --data '{"date":"2026-01-28","temperatureC":-9,"temperatureF":16,"summary":"Scorching"}' localhost:5062/weatherforecast
```


## HttpContext and ControllerContext (and others)

Each controller within ASP.net has access to context data that is relevant to the current connection. This can seem not very transparent initially, as we have a controller that is generated that inherits from `ControllerBase` but without knowing the properties and methods associated, we could make a poor assumption that is all that there is to know.

Typically we need to have access to a Database or parts of the request.

Associated with `Controller` is access to `HttpContext` which you can use the [documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/use-http-context?view=aspnetcore-10.0) to find methods and properties to use.

You can then also follow up to use `ControllerContext` which can give access to a database context and other associated objects/singletons. Refer to the [documentation here](https://learn.microsoft.com/en-us/dotnet/api/system.web.mvc.controllercontext?view=aspnet-mvc-5.2).



## Route Attribute and Routing

You would have observed with the controller the `Route` attribute. This attribute itself is used to outline the name and prefixing of the controller and methods associated. The attribute can be used for both classes and methods.

```
[Route("[controller]")]
```

The `[controller]` part is special phrase in ASP.NET where it will use the name of the class and remove the **Controller** portion from it. This can lead to some confusing issues that you will want to avoid however. In addition, we can change this and make it a prefix and set the `Route` per method.

```cs
[Route("/api/weather")]
public class WeatherForecastController : ControllerBase
{
  private static readonly string[] Summaries =
  [
      "Freezing", "Bracing", "Chilly", "Cool", "Mild", "Warm", "Balmy", "Hot", "Sweltering", "Scorching"
  ];

  [HttpPost(Name = "PostWeatherForecast")]
  [Route("/add")]
  public WeatherForecast Post([FromBody] WeatherForecast forecast)
  {
    return forecast;
  }
}
```

We can then observe the route changing and test if it is accessible using the following command.


```
curl -XPOST -H "Content-Type: application/json" --data '{"date":"2026-01-28","temperatureC":-9,"temperatureF":16,"summary":"Scorching"}' localhost:5062/api/weather/add
```

