import requests

def get_weather(city):
    api_key = "YOUR_API_KEY_HERE"  #  Replace with your OpenWeatherMap API key
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"

    try:
        response = requests.get(url)
        data = response.json()

        if response.status_code == 200:
            print(f"\n Weather in {data['name']}, {data['sys']['country']}")
            print(f"Temperature: {data['main']['temp']}°C")
            print(f" Condition: {data['weather'][0]['description'].title()}")
            print(f" Wind Speed: {data['wind']['speed']} m/s")
            print(f"🌡 Feels Like: {data['main']['feels_like']}°C\n")
        else:
            print("City not found. Please check the name.")
    except Exception as e:
        print("⚠️ Error:", e)

if __name__ == "__main__":
    print("🌦️ Welcome to Weather Forecast App")
    city_name = input("Enter city name: ")
    get_weather(city_name)
