## API with .NET

#### I hope this repository can serve as a reference for creating APIs using .NET


## Installing
- Installing the template with the controllers.
```
dotnet new webapi --use-controllers
```
- Run the api
```
dotnet run
```
- I create a folder with the Bruno config to test the API
- In Bruno, Postman or Insomnia test this endpoint
```
http://localhost:5098/WeatherForecast
```
- If this works everything is OK.
---

## Post and Delete
- Creation in controller static date in WeatherForecastController
```
    private static List<WeatherForecast> ListWeatherForecast = new List<WeatherForecast>();
```
- Add the logic need to return the list created static
- Add the POST and the DELETE
```

    [HttpPost]
    public IActionResult Post(WeatherForecast weatherForecast)
    {
        ListWeatherForecast.Add(weatherForecast);

        return Ok();
    }

    [HttpDelete("{index}")]
    public IActionResult Delete(int index)
    {
        ListWeatherForecast.RemoveAt(index);
        return Ok();
    }
```
- Run the api
```
dotnet run
```
- Test in Bruno, Postman or Insomnia 
```
POST
http://localhost:5098/WeatherForecast
DELETE
http://localhost:5098/WeatherForecast/2
```

## Manage Routes
- New Folder "webapi-NET" is the config of BRUNO (equivalent to Postman)
- In WeatherForecastController.cs 
```
[Route("[controller]")]
http://localhost:5098/WeatherForecast
[Route("api/[controller]")]
http://localhost:5098/api/WeatherForecast
```
- Also the routing in the action/functions
```
[Route("api/[controller]")]
    [HttpGet(Name = "GetWeatherForecast")]
    [Route("get/weatherforecast")]
    [Route("get/theweather")]
    public IEnumerable<WeatherForecast> Get()
    {
        return ListWeatherForecast;
    }
http://localhost:5098/api/weatherforecast/get/weatherforecast
or
http://localhost:5098/api/weatherforecast/get/theweather
```
- IMPORTANT is possible to add more than 1 Route to get the same result. 
- Other way is using [action] this will use the name of method in this case GetFull
```
[Route("api/[controller]")]
    [HttpGet]
    [Route("[action]")]
    public IEnumerable<WeatherForecast> Getfull()
    {
        return ListWeatherForecast;
    }
http://localhost:5098/api/weatherforecast/getfull
```

