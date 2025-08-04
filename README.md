# CineCraze - Modified for Local JSON Data

## Changes Made

This version of cinemax.html has been modified to:

1. **Remove encryption/decoding**: Eliminated base64 decoding functions that were used to decrypt remote data
2. **Remove TMDB API integration**: Removed all TMDB API calls and related functions
3. **Use local JSON data**: Modified to work with a local `pagsure.json` file

## Usage

1. Place your content data in `pagsure.json` in the same directory as `cinemax.html`
2. The JSON structure should follow this format:

```json
{
  "Categories": [
    {
      "MainCategory": "Movies",
      "Entries": [
        {
          "Title": "Movie Title",
          "Description": "Movie description",
          "Poster": "poster_url",
          "Thumbnail": "thumbnail_url",
          "Year": "2024",
          "Rating": "8.5",
          "Country": "USA",
          "Genre": "Action",
          "Servers": [
            {
              "Name": "Server 1",
              "Url": "streaming_url"
            }
          ]
        }
      ]
    }
  ]
}
```

3. Serve the files using a local web server (e.g., `python3 -m http.server`)
4. Open `cinemax.html` in your browser

## Features Removed

- Base64 data decoding
- TMDB API integration for fetching movie/series metadata
- Remote data source dependencies

## Features Retained

- All UI functionality
- Video player integration
- Search and filtering
- Responsive design
- Theme switching