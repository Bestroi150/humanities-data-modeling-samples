# Module 2: Spatial Data and Geographic Information Systems (GIS)

## Overview

Geographic data adds a spatial dimension to humanities research. Instead of just knowing *what* something is, we also know *where* it is. This module introduces spatial data formats, coordinate systems, and how to work with geographic information in digital humanities projects.

## Key Concepts

### Coordinates and Geometries

**Latitude and Longitude**
- **Latitude**: Measures north-south position (-90 to +90 degrees)
- **Longitude**: Measures east-west position (-180 to +180 degrees)
- **Example**: Ancient Athens is approximately at (37.9838° N, 23.7275° E)

**Types of Geometries**
- **Points**: A single coordinate (e.g., a city, inscription findspot)
- **Lines**: Connected coordinates (e.g., trade routes, boundaries)
- **Polygons**: Enclosed areas (e.g., regions, archaeological zones)

### Coordinate Reference Systems (CRS)

Different map projections and coordinate systems exist:
- **WGS84 (EPSG:4326)**: The standard for web mapping and GPS
- **UTM zones**: Regional projections for detailed mapping
- **Historical projections**: Custom systems for ancient or historical data

**Best practice**: Use WGS84 for interoperability with web tools.

## Data Formats for Spatial Data

### GeoJSON
**Format**: JSON with geographic properties
**Advantages**: Web-native, human-readable, widely supported
**Use case**: Web mapping, APIs

```json
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [23.7275, 37.9838]
  },
  "properties": {
    "ID": "001",
    "Region": "Attica",
    "Material": "Marble",
    "Date": "450 BCE"
  }
}
```

### Shapefile
**Format**: Binary format with multiple files (.shp, .dbf, .shx)
**Advantages**: Industry standard for GIS
**Use case**: Desktop GIS applications (ArcGIS, QGIS)

### KML (Keyhole Markup Language)
**Format**: XML-based
**Advantages**: Works with Google Earth, good for visualization
**Use case**: Google Earth, historical mapping

## Working with Geographic Data

### Combining Tabular and Spatial Data

Often you have:
- **Tabular data**: ID, Region, Material, Date (in CSV or spreadsheet)
- **Geographic data**: Latitude, Longitude (points on a map)

**Solution**: Add Latitude and Longitude columns to your CSV, then convert to GeoJSON.

### The Inscriptions Dataset Example

Starting with `inscriptions_clean.csv`:
```
ID | Region | Material | Date | Location | Latitude | Longitude
001 | Attica | Marble | 450 BCE | Athens | 37.9838 | 23.7275
002 | Boeotia | Bronze | 390 BCE | Orchomenos | 38.3247 | 23.0875
```

This becomes `inscriptions.geojson`:
```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [23.7275, 37.9838]
      },
      "properties": {
        "ID": "001",
        "Region": "Attica",
        "Material": "Marble",
        "Date": "450 BCE",
        "Location": "Athens"
      }
    }
    // ... more features
  ]
}
```

## Web-Based Mapping Tools

### Interactive Mapping Libraries
- **Leaflet.js**: Lightweight, open-source web mapping
- **Mapbox**: Modern vector mapping with styling
- **OpenStreetMap**: Free, community-driven basemap

### Creating a Web Map

Basic workflow:
1. Start with tidy tabular data (CSV)
2. Add geographic coordinates (latitude, longitude)
3. Convert to GeoJSON
4. Use a mapping library (Leaflet) to display
5. Add interactivity (popups, filtering, search)

## Ethical Considerations in Spatial Humanities

### Sacred Sites and Privacy
- **Avoid precise coordinates** for sacred or sensitive locations
- Document why precision might be problematic
- Consider generalization (e.g., region instead of exact point)

### Colonial Boundaries
- Modern nation-state borders don't match ancient political divisions
- Use historical boundary layers when appropriate
- Acknowledge anachronisms in mapping

### Representation Choices
- Map projections distort reality
- What you choose to map affects interpretation
- Document your design choices

## Hands-On Activity

### Part 1: Exploring GeoJSON
1. Open `inscriptions.geojson` in a text editor
2. Identify the structure: FeatureCollection, Features, geometry, properties
3. Find the coordinates for your favorite location

### Part 2: Interactive Mapping
1. Open `demo/map.html` in your browser
2. Interact with the map:
   - Click on markers to see inscription details
   - Use the search/filter features
   - Notice how tabular and geographic data are linked

### Part 3: Converting Data (Optional)
Try converting `inscriptions_clean.csv` to GeoJSON using an online tool or scripting

## Key Takeaways

- Geographic data combines coordinates with tabular information
- GeoJSON is the modern standard for web-based mapping
- Latitude and Longitude (WGS84) are the standard coordinate system
- Ethical considerations matter: think about precision, projection, and representation
- Combining spatial and tabular data enables powerful new research questions

## Further Reading

- Presner, Todd, & Shepard, Diane. "Mapping the Geospatial Turn." *A New Companion to Digital Humanities*, 2015.
- Leaflet.js Documentation: https://leafletjs.com/
- GeoJSON Specification: https://tools.ietf.org/html/rfc7946

## Next Steps

Move to Module 3 to learn how to convert between different data formats while preserving all information and meaning.
