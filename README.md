# Charis Web Services

Secure, server-side proxy endpoints for third-party APIs, built with charm, beauty, and a touch of creativity ✨

This backend service allows portfolios and personal websites to safely integrate external services without exposing API keys or tokens client-side.

All endpoints include validation, timeouts, robust error handling, temporary file cleanup, and performance-focused caching.

All requests **must be authenticated** using a **User API Token** generated from your dashboard profile.

## Authentication

You must include **both** of the following headers:

```
Authorization: Bearer YOUR_CHARIS_TOKEN
x-api-secret: YOUR_CHARIS_SECRET
```

## Available Endpoints

### 1. Media Proxy
Secure Cloudinary operations: gallery fetch, file upload, and metadata update.

- **Method**: `POST https://api.charisprod.xyz/v1/media`
- **Content-Type**:
  - `application/json` for `gallery` and `update-metadata`
  - `multipart/form-data` for `upload` (includes file)

**Actions**:
- `gallery` – List media in a folder
- `upload` – Upload a new file with optional metadata
- `update-metadata` – Update existing resource metadata

**Common fields** (JSON or form fields):
```json
{
  "action": "gallery", // or "upload" or "update-metadata"
  "cloudName": "your-cloud-name",
  "apiKey": "your-api-key",
  "apiSecret": "your-api-secret"
}
```

### Additional fields by action

| Action          | Field        | Type / Notes | Default / Example       |
|-----------------|--------------|--------------|-------------------------|
| gallery         | folder       | Required    | `optional/folder/path` |
| upload          | file         | Required    | —                       |
| upload          | alt          | Optional    | —                       |
| upload          | aspectRatio  | Optional    | `16/9`                  |
| upload          | folder       | Optional    | —                       |
| upload          | upload_preset| Required    | —                       |
| update-metadata | alt          | Optional    | —                       |
| update-metadata | aspectRatio  | Optional    | `16/9`                  |

### 2. Weather Proxy
Current weather data with flexible location options.

- **Method**: `GET https://api.charisprod.xyz/v1/weather`
- **Query parameters** (use exactly one location selector):

| Parameters | Description          | Type      | Example                              |
|------------|----------------------|-----------|--------------------------------------|
| lat + lon | Coordinates          | —         | ?lat=-6.2088&lon=106.8456            |
| q         | City Name            | —         | ?q=Jakarta                           |
| id        | OpenWeather city ID  | —         | ?id=1621177                          |
| zip       | ZIP / Postal Code    | —         | ?zip=94040,US                        |
| units     | Temperature Units    | `metric`<br>`imperial`<br>`standard` | &units=metric                        |
| apiKey    | Your OpenWeatherMap API key | Optional | &apiKey=${process.env.WEATHER_API_KEY} |

- **Example**: `GET https://api.charisprod.xyz/v1/weather?q=Jakarta&apiKey=${process.env.WEATHER_API_KEY}`
- **Features**: CORS enabled, 10-minute edge/CDN caching (`s-maxage=600`)

### 3. Spotify Proxy
Secure Spotify data: top tracks and currently playing (with Last.fm fallback for top tracks).

- **Top Tracks**: `POST https://api.charisprod.xyz/v1/topMusic`
- **Now Playing**: `POST https://api.charisprod.xyz/v1/nowPlaying`

**Request body** (JSON):
```json
{
  "apiKey": "your-spotify-client-id",
  "apiSecret": "your-spotify-client-secret",
  "refreshToken": "firebase-stored-refresh-token",
  "userId": "your-spotify-user-id",
  // Required only for topMusic:
  "lastfmKey": "your-lastfm-api-key",
  "lastfmUser": "your-lastfm-username"
}
```

## Why Use Charis Web Services?

- **Maximum security**: Sensitive keys and tokens stay server-side
- **Reliable & robust**: Timeouts, cleanup, detailed logging & error responses
- **Optimized performance**: Efficient proxying, caching headers
- **Personal-focused**: Designed specifically for portfolios and personal websites

## Documentation

Detailed integration guides with code examples for Next.js, Gatsby, and Astro:

- [Cloudinary Media Management](https://charisprod.xyz/apis/cloudinary)
- [Weather Data Fetching](https://charisprod.xyz/apis/weather)
- [Spotify Music Integration](https://charisprod.xyz/apis/spotify)

Built with charm, beauty, and a touch of creativity ✨
