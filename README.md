# Weather app

A React page in `frontend/` and a Spring Boot API in `backend/`. You type a city. The page asks this API, and the API asks OpenWeatherMap for the current weather in Celsius.

`frontend/src/components/WeatherComponent.js` is the whole page. Get Weather asks port 8080 for `/weather/` plus the city name. A successful response shows the city, the weather icon, the description, the temperature, and the humidity. A failed request is logged in the console, and the previous result is cleared. The page itself stays on the form.

`WeatherController` handles `GET /weather/{city}`. It calls OpenWeatherMap's current-weather endpoint with `units=metric` and returns that body. The key is the property `openweathermap.apikey` in `backend/src/main/resources/application.properties`.

`CorsConfig` allows the React dev origin with a slash on the end. The browser sends that origin without the slash, so the rule does not match the dev page.

## Run

The API is Spring Boot 3.1.2 on Java 17. From `backend/`:

```bash
./mvnw spring-boot:run
```

It listens on port 8080. There is no `server.port` in the properties file.

From `frontend/`:

```bash
npm install
npm start
```

The dev server prints the address to open.
