# Module 3: Format Conversion and Interoperability

## Overview

The same dataset can be represented in multiple formats: CSV, JSON, XML, GeoJSON. Each format has strengths and uses. This module teaches you to convert between formats while preserving semantic meaning and data integrity.

## Why Format Conversion Matters

Different tools and workflows require different formats:
- **Spreadsheet analysis** → CSV
- **Web applications** → JSON or GeoJSON
- **Archival preservation** → XML
- **GIS mapping** → GeoJSON or Shapefile
- **Document encoding** → XML or TEI

Converting between formats enables:
- Data reuse across tools
- Integration of diverse sources
- Long-term preservation
- Collaboration across disciplines

## Understanding Each Format

### CSV (Comma-Separated Values)
**Structure**: Rows and columns, one row per record
**Best for**: Tabular data, spreadsheet analysis
**Limitations**: No hierarchical data, requires careful escaping of special characters

```csv
ID,Region,Material,Date,Location,Latitude,Longitude
001,Attica,Marble,450 BCE,Athens,37.9838,23.7275
002,Boeotia,Bronze,390 BCE,Orchomenos,38.3247,23.0875
```

### JSON (JavaScript Object Notation)
**Structure**: Key-value pairs, nested objects and arrays
**Best for**: Web APIs, modern applications, flexible data structures
**Strength**: Human-readable yet machine-parseable

```json
{
  "inscriptions": [
    {
      "ID": "001",
      "Region": "Attica",
      "Material": "Marble",
      "Date": "450 BCE",
      "Location": "Athens",
      "Coordinates": {
        "Latitude": 37.9838,
        "Longitude": 23.7275
      }
    }
  ]
}
```

### GeoJSON
**Structure**: JSON with geographic geometry
**Best for**: Web mapping, spatial visualization
**Key feature**: Integrates coordinates with feature properties

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
  ]
}
```

### XML (Extensible Markup Language)
**Structure**: Hierarchical tags with nested elements
**Best for**: Document markup, archival standards (TEI, EAD)
**Strength**: Explicit semantics, customizable schemas

```xml
<?xml version="1.0" encoding="UTF-8"?>
<inscriptions>
  <inscription>
    <ID>001</ID>
    <Region>Attica</Region>
    <Material>Marble</Material>
    <Date>450 BCE</Date>
    <Location>Athens</Location>
    <Coordinates>
      <Latitude>37.9838</Latitude>
      <Longitude>23.7275</Longitude>
    </Coordinates>
  </inscription>
</inscriptions>
```

## Conversion Workflows

### CSV → JSON

**Process**:
1. Read CSV row by row
2. Convert each row to a JSON object
3. Group objects in an array

**Preserves**: All data values
**Loses**: No loss (JSON can represent all CSV data)

### JSON → CSV

**Process**:
1. Extract all unique keys from objects
2. Create CSV header row
3. Convert each object to a CSV row

**Preserves**: Flat data relationships
**Loses**: Nested structures (flatten with dot notation or separate tables)

### CSV/JSON → XML

**Process**:
1. Create root element (`<inscriptions>`)
2. For each record, create a child element (`<inscription>`)
3. Add field values as child elements or attributes

**Preserves**: All data values, semantic relationships
**Loses**: None (XML can represent any structured data)

### Adding Geographic Data

**CSV with coordinates → GeoJSON**:
1. Start with CSV containing Latitude/Longitude columns
2. Create GeoJSON structure
3. Map Latitude → coordinates[1], Longitude → coordinates[0]
4. Map all other columns to `properties` object

**Important**: GeoJSON uses [Longitude, Latitude] order (opposite of conventional notation!)

## Conversion Tools and Methods

### Online Tools (No Programming Required)
- **Mapshaper**: Convert between formats, simplify geometries
- **CloudConvert**: General file format conversion
- **Online GeoJSON tools**: Specific for geographic data

### Spreadsheet Method
1. Open CSV in Excel/Calc
2. Use formulas to generate JSON or XML syntax
3. Export as text
4. Clean up as needed

### Command-Line Tools
```bash
# Using jq (JSON query tool)
# Using xmlstarlet (XML processing)
# Using Python or Node.js scripts
```

### Python Example (Simple)
```python
import csv
import json

# CSV to JSON
with open('inscriptions.csv', 'r') as f:
    reader = csv.DictReader(f)
    data = list(reader)

with open('inscriptions.json', 'w') as f:
    json.dump(data, f, indent=2)
```

## Mapping Conversions

### Semantic Mapping
When converting, ensure that the meaning is preserved:

| CSV Column | JSON Key | XML Element | Meaning |
|-----------|----------|-------------|---------|
| ID | id | `<ID>` | Unique identifier |
| Region | region | `<Region>` | Geographic region |
| Material | material | `<Material>` | Physical material |
| Date | dateValue | `<Date>` | Approximate date |

### Handling Complex Data

**CSV Problem**: How do you represent multiple values per record?

**Solutions**:
1. **Separate rows**: Each material in a separate row with duplicate other fields
2. **Array column**: Use JSON for multiple materials: `["Marble", "Bronze"]`
3. **Separate table**: Create a linking table (invoices ↔ line items)

## Best Practices for Conversion

1. **Validate before conversion**
   - Ensure data is tidy and clean
   - Check for missing values
   - Verify consistent formatting

2. **Document the mapping**
   - Keep a record of which fields map to which
   - Note any transformations applied
   - Record the date and tool used

3. **Test the conversion**
   - Compare record counts before and after
   - Spot-check several records
   - Verify special characters are handled correctly

4. **Preserve metadata**
   - Include source information
   - Document the original format
   - Add creation date and provenance

5. **Use standards**
   - Follow GeoJSON specification (RFC 7946)
   - Use established XML schemas (TEI, EAD)
   - Prefer standard formats over custom ones

## Hands-On Activity

### Part 1: Explore Multiple Formats
Open each of these files and compare:
- `data/inscriptions_clean.csv`
- `data/inscriptions.json`
- `data/inscriptions.geojson`
- `data/inscriptions.xml`

**Questions**:
- What information appears in all formats?
- What is unique to each format?
- How would you recover from CSV to XML?

### Part 2: Manual Conversion
Pick one inscription record and manually convert it:
- Start with CSV
- Convert to JSON
- Then convert to XML

Check your work against the provided files.

### Part 3: Verify Equivalence
Write out one inscription in all four formats. Ensure all information is present in each version.

## Key Takeaways

- Multiple formats serve different purposes
- CSV is best for tabular analysis
- JSON is best for web applications
- XML is best for complex markup and archival
- GeoJSON is best for web mapping
- Format conversion should preserve semantic meaning
- Always document and validate your conversions

## Common Pitfalls

**Don't** lose data during conversion  
**Don't** assume formats are equivalent without checking  
**Don't** forget that GeoJSON coordinates are [Lon, Lat]  
**Don't** skip validation after conversion  

**Do** test conversions on sample data first  
**Do** document your mapping decisions  
**Do** preserve metadata and provenance  
**Do** use standard schemas and formats  

## Further Reading

- JSON Specification: https://www.json.org/
- GeoJSON Specification (RFC 7946): https://tools.ietf.org/html/rfc7946
- XML Specification: https://www.w3.org/XML/
- CSV Specification (RFC 4180): https://tools.ietf.org/html/rfc4180
- Flanders & Jannidis, *The Shape of Data in the Digital Humanities*

## Next Steps

You now have a foundation in data formats! Explore the demo (`demo/map.html`) to see all these concepts integrated in a real web application.
