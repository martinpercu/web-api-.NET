
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
- Test in