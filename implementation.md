# Grade 12 Graduation Project — Interactive HTML Page

## Overview
A single self-contained `index.html` file that can be embedded on a GitHub Page. It features:
1. **Welcome Screen** — animated starfield with a graduation emblem and title
2. **Door Opening Animation** — CSS 3D perspective doors swing open to reveal the map
3. **Interactive Room Map** — recreation of the H315 floor plan with 8 clickable subject zones
4. **Project Cards Modal** — clicking a zone shows all projects in that category with student names and supervisor
5. **Grade 12 Topics Directory** — a master modal displaying all projects grouped by academic field and color-coded
6. **Grading Rubric Tool** — an interactive grading utility that calculates final scores and simplifies evaluation

## Data Sources
| File | Purpose |
|------|---------|
| `Screenshot 2026-05-15 162933.png` | Visual reference for map layout (H315 floor plan) |
| `Grade 12 TOPICS.docx` | Project titles grouped by academic category |
| `Group, Student Names, Project Title and Supervisor Name (1).xlsx` | Excel spreadsheet with official group numbers, student names, project titles, and supervisor names |

## Map Zones (from screenshot)
| Zone | Position on Map | Category Mapped | Color Code (RGB) |
|------|----------------|-----------------|------------------|
| CS/Media Arts | Top-center-left | Computer Science / AI | 192, 57, 43 |
| Social Studies/Sociology | Top-center-right | Social Studies / Sociology | 26, 82, 118 |
| Math/Sciences/Engineering | Left side (vertical) | Math / Sciences / Engineering | 108, 52, 131 |
| Economics | Bottom-left | Economics | 30, 132, 73 |
| Arts | Bottom-center | Arts | 183, 149, 11 |
| Psychology/Health | Right-lower (vertical) | Psychology / Health | 232, 67, 147 |
| Business/Marketing | Right-middle (vertical) | Business / Marketing | 0, 137, 123 |
| History/Geography | Right-bottom (vertical) | History / Geography | 230, 126, 34 |

## Tech Stack
- **Pure HTML/CSS/JS** — no build tools, no dependencies
- **Google Fonts**: Outfit (headings), Inter (body)
- **CSS Features**: gradients, backdrop-filter, 3D transforms, keyframe animations, rotated text zones (180deg)
- **Responsive**: viewport-based scale-factor scaling for H315 map layout, flex layouts, mobile media queries

## How to Replicate
1. **Extract Project Data**: Parse the Excel spreadsheet using a Python script (with `pandas` or `openpyxl`). To handle merged cells, forward fill (`ffill()`) empty cells in the 'Group', 'FYP Project Title', and 'Supervisor Name' columns.
2. **Classify Projects**: Categorize the groups into the 8 major disciplines (CS, Social Studies, Math/Sciences/Engineering, Economics, Arts, Psychology, Business, History). 
   - Note: Environmental topics like "Invasive Species" belong under *Math / Sciences / Engineering*. 
   - Creative and media projects (Art History, Film depiction, Sad Art, Traditional Arts) belong under the *Arts* category.
3. **Build the DATA Object**: Populate the javascript `DATA` object structure containing all 40 unique groups.
4. **Layout Setup**: Position the `.zone` divs absolutely inside the map container matching their physical room H315 locations.
5. **Welcome & Door Interaction**: Write CSS animations for the space starfield, credit badge, and 3D folding doors.
6. **Tabs & Directories**: Wire buttons for "Project Map", "All Topics", and "Grading Rubric". Make sure "All Topics" displays student names in a `👤 Students:` format.
7. **TDD Validation**: Write a verification script (`test_tdd.py`) to assert that:
   - All Excel groups are accounted for in `index.html`.
   - The obsolete `socsci` key is replaced by `arts`.
   - Projects are categorized in their proper fields.

## Embedding on GitHub Pages
1. Commit the final `index.html` to both your `main` and `master` branches (especially if GitHub Pages is configured to deploy from `master`).
2. Give GitHub Pages up to 1-2 minutes to compile the build, then perform a hard-refresh (`Ctrl + F5` or `Cmd + Shift + R`) to preview.
