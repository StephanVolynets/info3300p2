# Global Health & Demographic Trends Visualization

**CS 3300 – Project 2**  
**Team:** Fedinard Nyanyo (fen7), Justin Wong (jsw345), Merry Zebro (mz289),  Stephan Volynets (svv6) 
**Cornell University**  
**Project Duration:** October 2024 – November 2024

---

## Overview

This project visualizes global life expectancy and population trends from 1960 to 2022. The interactive web application allows users to explore how these two key metrics have evolved over six decades for different countries. By combining multiple datasets and employing advanced data processing techniques, the visualization offers a comprehensive look at global health and demographic changes.
![Xnip2025-02-16_17-21-25](https://github.com/user-attachments/assets/35a23947-c10b-46d3-8684-2a44a82aba4e)

---

## Data Description

- **Life Expectancy Data:**  
  Annual life expectancy for each country from 1960 to 2022, sourced from the World Bank Group.

- **Population Data:**  
  Annual population figures for the same time frame, sourced from Our World In Data.

- **Geospatial Data:**  
  A world map in TopoJSON format (excluding Antarctica) from GitHub, augmented with the above datasets. The processed JSON file (`combined_data.json`) includes:
  - Life expectancy and population data for each country/year stored in the “properties” of each country.
  - A list of all recorded life expectancy values along with the minimum and maximum, used to generate color scales.

---

## Data Processing

Data processing was handled by two JavaScript scripts:

- **processLifeExpData.js:**  
  - Reads the life expectancy CSV and TopoJSON files.  
  - Matches country names (with adjustments for inconsistencies, e.g., “Congo, Dem. Rep.” vs. “Democratic Republic of the Congo”) and creates a dictionary mapping years to life expectancy values for each country.  
  - Computes the minimum, maximum, and full list of life expectancy values, and integrates this information into the TopoJSON’s `properties`.

- **processPopulationData.js:**  
  - Reads population data and aligns it with the life expectancy data in the TopoJSON file.  
  - Uses a lookup dictionary and a mapping (`countryNameMap`) to resolve differences in country names.  
  - Merges the datasets into a single JSON structure for easy access during visualization.

---

## Visual Design & Interaction

### Map Visualization

- **Interactive Map:**  
  Uses a Mercator projection to display a world map with overlaid data on life expectancy and population.
  
- **Color Scales:**  
  - **Life Expectancy:**  
    A linear color scale with green indicating higher life expectancy and red indicating lower values.
  - **Population:**  
    A logarithmic color scale where red represents heavily populated countries and blue represents less populated regions.
  
- **User Controls:**  
  - A slider to select a year, with an accompanying label showing the current year.
  - Play and stop buttons to animate the timeline.
  - A text box to input a specific year directly.
  - Zoom and pan functionality for detailed exploration.
  - Clickable countries to zoom in for more details.
  - A reset button to restore the initial view.

### Scatterplot Visualization

- **Correlation Analysis:**  
  Presents a scatterplot with life expectancy on the y-axis and population on the x-axis (log-scaled) to highlight the correlation between the two.
  
- **Interactive Elements:**  
  - Tooltips displaying country name, life expectancy, population, and year when hovering over data points.
  - Dynamic circle sizes based on population, enabling easy comparison of different countries.
  - Gridlines and axis labels for clarity.

---

## Visual Design Rationale

- **Map Choice:**  
  A map was chosen because it naturally represents country-level data and allows for an intuitive understanding of global trends.  
- **Color Choices:**  
  Green-to-red for life expectancy makes the differences visually distinct, while a log scale for population avoids overwh
