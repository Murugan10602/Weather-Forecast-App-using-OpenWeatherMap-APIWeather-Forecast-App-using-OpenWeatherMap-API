# Weather-Forecast-App-using-OpenWeatherMap-APIWeather
# Example code: Weather Forecast App using OpenWeatherMap API
import requests

def get_weather(city):
    api_key = "YOUR_API_KEY"
    base_url = "https://api.openweathermap.org/data/2.5/weather"

    params = {
        "q": city,
        "appid": api_key,
        "units": "metric"  # Use "imperial" for Fahrenheit
    }

    response = requests.get(base_url, params=params)
    data = response.json()

    if data["cod"] == 200:
        temperature = data["main"]["temp"]
        description = data["weather"][0]["description"]
        print(f"Weather in {city}: {temperature}°C, {description}")
    else:
        print("City not found.")

city_name = input("Enter city name: ")
get_weather(city_name)
