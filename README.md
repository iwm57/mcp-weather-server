# MCP Weather Server

A Model Context Protocol (MCP) server that provides weather data tools using the US National Weather Service API.

## Features

- **get_alerts**: Get active weather alerts for any US state
- **get_forecast**: Get detailed weather forecast for any location (latitude/longitude)

## Installation

```bash
# Clone the repository
git clone https://github.com/iwm57/mcp-weather-server.git
cd mcp-weather-server

# Install dependencies
uv add "mcp[cli]" httpx
```

## Usage

### Running the Server

```bash
uv run weather.py
```

### Available Tools

#### get_alerts(state)
Get weather alerts for a US state.

**Parameters:**
- `state` (str): Two-letter US state code (e.g. CA, NY, TX)

**Example:**
```python
await get_alerts("CA")
```

#### get_forecast(latitude, longitude)
Get weather forecast for a location.

**Parameters:**
- `latitude` (float): Latitude of the location
- `longitude` (float): Longitude of the location

**Example:**
```python
await get_forecast(38.5816, -121.4944)  # Sacramento, CA
```

## Claude for Desktop Configuration

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/mcp-weather-server",
        "run",
        "weather.py"
      ]
    }
  }
}
```

## API

This server uses the [National Weather Service API](https://www.weather.gov/documentation/services-web-api) which is free and requires no API key.

**Note:** This service only provides weather data for US locations.

## License

MIT
