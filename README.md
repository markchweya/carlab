# CarLab 🚗📊
**Performance. Style. Trade-offs.**  
A Shiny app that helps users compare cars in seconds using (1) a preference-based ranking score and (2) a multivariate PCA + clustering view.

## Live Demo
- App: https://markchweya.shinyapps.io/carlab/

## What CarLab does
CarLab lets you:
- **Rank cars by your preferences** (e.g., prioritize mpg, horsepower, lightweight, or faster acceleration)
- **Filter the dataset** (e.g., cylinders, transmission type, minimum mpg)
- **Explore trade-offs visually** using **PCA** (dimensionality reduction)
- **Group similar cars** using **k-means clustering** on PCA scores
- **Inspect the raw data** behind the visuals

## Key Features
### 1) Preference-based ranking
Move sliders to set how much you care about:
- Fuel economy
- Engine power
- Lightweight build
- Fast acceleration

CarLab combines the selected factors into a single score and returns a ranked “best match” list.

### 2) Multivariate analytics (PCA + Clustering)
- Choose which variables to include in PCA
- View a 2D performance map (PC1 vs PC2)
- See explained variance per component
- Understand feature influence (loadings)
- See cluster profiles for interpretability

## Data
The app is built around a compact car-performance dataset with variables such as:
- mpg, hp, wt, qsec, drat (and related metadata like cylinders/transmission)

## Tech Stack
- **R**
- **Shiny**
- Typical supporting packages: `ggplot2`, `dplyr`, `stats` (PCA + kmeans), and UI helpers (depending on your implementation)

## How it works (high-level)
1. **Normalize/scale** numeric features (so variables are comparable).
2. **Preference score**: weight features based on slider priorities → compute a composite score → rank cars.
3. **PCA**: reduce selected variables into principal components for 2D visualization.
4. **Clustering**: run k-means on PCA scores (PC1–PC2) to group similar cars.

## Run locally
### Option A: RStudio (recommended)
1. Download/clone this repo
2. Open the project in RStudio
3. Install dependencies (if needed)
4. Run:
```r
shiny::runApp()
