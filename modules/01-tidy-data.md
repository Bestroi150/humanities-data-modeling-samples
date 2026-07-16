# Module 1: Principles of Tidy Data

## Overview

Tidy data is a fundamental concept in data analysis and management. A well-structured, "tidy" dataset makes it easy to analyze, visualize, and share information. This module introduces the principles of tidy data and demonstrates how to identify and fix common data quality issues.

## What is Tidy Data?

Tidy data follows three key principles:

1. **Each variable forms a column**
   - Every attribute or property gets its own column
   - Example: `Region`, `Material`, `Date` are separate columns

2. **Each observation forms a row**
   - Every record or instance gets its own row
   - Example: Each inscription is one row

3. **Each type of observational unit forms a table**
   - Don't mix different types of data in one table
   - Example: Keep inscriptions, locations, and people in separate tables if they represent different entity types

## Why Tidy Data Matters

### Advantages
- **Easier to analyze**: Consistent structure enables simple queries and calculations
- **More shareable**: Others can quickly understand your data
- **Better for tools**: Most analysis software assumes tidy format
- **Reproducible**: Standard structure supports automation and reproducibility
- **FAIR principles**: Tidy data is more findable, accessible, and interoperable

## Common Data Quality Issues

### 1. Multiple Values in One Cell
**Problem**: `Location: "Athens, Corinth, Thebes"`
**Solution**: Create separate rows or use a separate relationship table

### 2. Mixed Data Types in a Column
**Problem**: `Date` column contains "450 BCE", "5th century", "uncertain"
**Solution**: Create separate columns for `Date_Value`, `Date_Type`, and `Date_Certainty`

### 3. Inconsistent Formatting
**Problem**: `Region: "Attica"`, `Region: "ATTICA"`, `Region: "attica"`
**Solution**: Standardize to one format (preferably lowercase or title case consistently)

### 4. Merged Cells or Missing Headers
**Problem**: Visual formatting that breaks data structure
**Solution**: Use one row for headers, avoid merged cells

### 5. Non-Data Rows
**Problem**: Blank rows, summary rows, or notes mixed with data
**Solution**: Keep data separate from metadata and annotations

### 6. Abbreviations and Shorthand
**Problem**: Inconsistent use of abbreviations (e.g., "Att." vs. "Attica")
**Solution**: Use full, standardized names

## Example: Before and After

### Messy Data
```
Inscription Data
ID | Find Location | Material(s) | Date | Description
001 | Athens/Piraeus | Marble | ~450 | Funerary, possibly Athenian
002 | Boeotia | Bronze, Iron | 400-380 | Honorific
| | | |
TOTAL: 2 inscriptions
```

### Tidy Data
```
ID | Region | Location | Material | Date_Value | Date_Type | Text_Type
001 | Attica | Athens | Marble | 450 | approximate | Funerary
002 | Boeotia | Orchomenos | Bronze | 390 | range | Honorific
```

## Hands-On Activity

Open the file `inscriptions_messy.csv` in a spreadsheet application:

1. **Identify issues**: What problems do you see?
2. **Document them**: List each issue
3. **Create a cleaning plan**: How would you fix each issue?
4. **Optional**: Create a cleaned version following tidy data principles

## Key Takeaways

- Tidy data is essential for analysis and sharing
- Consistency matters more than perfect formatting
- Plan your data structure before entering data
- One table per entity type
- Use separate rows for multiple values, not separate columns

## Further Reading

- Wickham, Hadley. "Tidy Data." *Journal of Statistical Software* 59, no. 10 (2014).
- GitHub: https://github.com/hadley/tidy-data/

## Next Steps

Move to Module 2 to learn how geographic data adds a spatial dimension to humanities datasets.
