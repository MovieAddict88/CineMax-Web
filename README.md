# CineCraze - Modified for Local JSON Data

## Changes Made

This version of cinemax.html has been modified to:

1. **Remove encryption/decoding**: Eliminated base64 decoding functions that were used to decrypt remote data
2. **Remove TMDB API integration**: Removed all TMDB API calls and related functions
3. **Use local JSON data**: Modified to work with a local `pagsure.json` file

## Files Included

- **`cinemax.html`** - Main application file (modified)
- **`pagsure.json`** - Sample content data file
- **`test_json.html`** - Test page to verify JSON structure
- **`README.md`** - This documentation

## Usage

### Quick Start
1. Place your content data in `pagsure.json` in the same directory as `cinemax.html`
2. Start a local web server: `python3 -m http.server 8080`
3. Open `http://localhost:8080/cinemax.html` in your browser
4. Optionally test the JSON first: `http://localhost:8080/test_json.html`

### JSON Structure
The `pagsure.json` file should follow this format:

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

### Data Requirements

**Required Fields for Movies:**
- `Title`, `Description`, `Poster`, `Thumbnail`, `Servers`

**Required Fields for TV Series:**
- `Title`, `Description`, `Poster`, `Thumbnail`, `Seasons`
- Each season must have `Episodes` array
- Each episode must have `Title`, `Servers`

**Required Fields for Live TV:**
- `Title`, `Description`, `Poster`, `Thumbnail`, `Servers`

**Optional Fields:**
- `Year`, `Rating`, `Country`, `Genre`, `SubCategory`

### Video URLs
The sample data uses Google's sample videos for demonstration. Replace the URLs in `Servers` arrays with your actual video content URLs. Supported formats:
- MP4 videos
- HLS streams (.m3u8)
- DASH streams (.mpd)
- Direct video URLs

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
- Carousel with featured content
- Episode navigation for TV series
- Multiple server support
- Picture-in-picture mode
- Fullscreen support

## Troubleshooting

### Common Issues

1. **"Data loading failed" error**
   - Ensure `pagsure.json` exists in the same directory as `cinemax.html`
   - Check that the JSON is valid using `test_json.html`
   - Verify you're serving files through a web server (not opening directly in browser)

2. **No content appears**
   - Check browser console for errors (F12)
   - Verify the JSON structure matches the expected format
   - Ensure Categories array exists and has proper MainCategory values

3. **Videos don't play**
   - Check that video URLs in `Servers` are accessible
   - Verify video format is supported by the browser
   - Some URLs may require CORS headers

4. **CORS errors**
   - Use a proper web server instead of opening files directly
   - For development: `python3 -m http.server 8080`
   - For production: Use Apache, Nginx, or similar

### Browser Compatibility
- Modern browsers with ES6+ support
- Chrome 60+, Firefox 55+, Safari 11+, Edge 79+