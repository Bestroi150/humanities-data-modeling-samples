# Thinking in Data: Empowering Humanities Students Through Structured Methods

**An interactive demonstration of data formats in Digital Humanities**

This repository contains teaching materials and sample data demonstrating how humanities data can be represented and processed across multiple formats: tabular data (CSV), spatial data (GeoJSON), structured markup (XML), and modern web formats (JSON).

## Overview

This project is based on the **Foundations of Humanities Data Modeling and Formats** curriculum and showcases practical, hands-on examples of data format conversion and interoperability. The demo uses a dataset of ancient inscriptions to illustrate key concepts in data organization, geographic information systems (GIS), and format conversion.

## Repository Structure

```
dh26-data-formats-demo/
├── README.md                      # This file
├── LICENSE                        # MIT License
├── CITATION.cff                   # Citation metadata for the project
├── modules/                       # Teaching modules
│   ├── 01-tidy-data.md           # Principles of tidy data
│   ├── 02-spatial-data.md        # Geographic data and GIS concepts
│   └── 03-format-conversion.md   # Converting between formats
├── data/                          # Sample dataset in multiple formats
│   ├── inscriptions_messy.csv    # Raw, unclean data
│   ├── inscriptions_clean.csv    # Cleaned, tidy data
│   ├── inscriptions.geojson      # Geographic data format
│   ├── inscriptions.json         # Modern web format
│   └── inscriptions.xml          # Structured markup format
└── demo/                          # Interactive demonstrations
    └── map.html                   # Interactive web-based map viewer
```

## Quick Start

1. **Explore the modules** – Start with `modules/01-tidy-data.md` to learn data organization principles.
2. **Examine the data** – Compare `inscriptions_messy.csv` with `inscriptions_clean.csv` to see data cleaning in practice.
3. **Try the interactive demo** – Open `demo/map.html` in your browser to explore geographic visualization.
4. **Convert formats** – Use `modules/03-format-conversion.md` to learn how to transform between formats.

## Key Concepts

### 1. Tidy Data Principles
- One observation per row
- One variable per column
- Consistent formatting and naming
- Proper handling of missing values

### 2. Spatial Data & GIS
- Representing geographic information (coordinates, geometries)
- GeoJSON for web-based mapping
- Linking tabular data with geographic locations

### 3. Format Conversion
- CSV ↔ JSON ↔ XML transformations
- Preserving semantic meaning across formats
- Choosing the right format for your data

## The Inscriptions Dataset

This demo uses a sample of ancient inscriptions with the following fields:

- **ID**: Unique identifier
- **Region**: Geographic region (Attica, Boeotia, etc.)
- **Material**: Material type (Marble, Bronze, etc.)
- **Date**: Approximate date of inscription
- **Text Type**: Funerary, Honorific, Dedication, etc.
- **Location**: Place name where found
- **Latitude/Longitude**: Geographic coordinates (for mapping)

### Data Formats Included

| Format | File | Use Case |
|--------|------|----------|
| **CSV** | `inscriptions_messy.csv`, `inscriptions_clean.csv` | Tabular data, spreadsheet analysis |
| **GeoJSON** | `inscriptions.geojson` | Web-based mapping, geographic visualization |
| **JSON** | `inscriptions.json` | Modern web APIs, database imports |
| **XML** | `inscriptions.xml` | Structured markup, document-oriented systems |

## Interactive Demo

The `demo/map.html` file provides an interactive web-based map viewer that:
- Displays inscriptions on a map using Leaflet.js
- Shows tabular data alongside geographic visualization
- Demonstrates real-time filtering and search
- Illustrates the relationship between tabular and geographic data

**To use:** Simply open `map.html` in any modern web browser.

## Learning Objectives

By working through this repository, you will:

- ✓ Understand what constitutes tidy, well-structured data
- ✓ Learn to recognize and fix common data quality issues
- ✓ Work with geographic data and spatial visualization
- ✓ Convert between multiple data formats while preserving meaning
- ✓ Apply FAIR data principles (Findable, Accessible, Interoperable, Reusable)
- ✓ Gain practical experience with humanities data workflows

## Technologies

- **Spreadsheets**: Excel, LibreOffice Calc, Google Sheets
- **Mapping**: Leaflet.js, GeoJSON
- **Data Processing**: CSV, JSON, XML
- **Browser**: HTML5, JavaScript

## FAIR Data Principles

This project adheres to FAIR data principles:

- **Findable**: Clear metadata and documentation
- **Accessible**: Open formats and free tools
- **Interoperable**: Data available in multiple formats
- **Reusable**: Open license and clear documentation of methods

## Citation

If you use this material in your research or teaching, please cite:

```bibtex
@software{thinking_in_data_2026,
  title={Thinking in Data: Empowering Humanities Students Through Structured Methods},
  author={Bestroi150},
  year={2026},
  url={https://github.com/Bestroi150/thinking-in-data}
}
```

Or see `CITATION.cff` for additional citation formats.

## License

This project is licensed under the Creative Commons Attribution 4.0 International License. See [LICENSE](LICENSE) for details.

You are free to share and adapt this material with proper attribution.

## Further Reading

- Flanders & Jannidis, *The Shape of Data in the Digital Humanities*
- D'Ignazio & Klein, *Data Feminism*
- Posner, Miriam. "Humanities Data: A Necessary Contradiction?"
- Kansa, Eric. "Open Context and the Archaeology of the Future"

## Contributing

Contributions are welcome! Please feel free to:
- Report issues
- Suggest improvements
- Add additional sample datasets
- Improve documentation

## Contact

For questions or comments, please open an issue on GitHub or contact the project maintainers.

---

**Last Updated**: 2026
**Maintainer**: Kristiyan Simeonov
