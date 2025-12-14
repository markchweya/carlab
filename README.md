# CarLab 🚗✨ 

CarLab is an interactive **R Shiny** web app for comparing cars using:
1) a **preference-based FitScore ranking**, and  
2) a multivariate **PCA + k-means clustering** view to understand performance trade-offs.

Live app: https://markchweya.shinyapps.io/carlab/

---

## What the app does

### ✅ Compare (FitScore ranking)
- Set your priorities (dropdown levels):  
  - Fuel economy (mpg)  
  - Engine power (hp)  
  - Lightweight (lower `wt`)  
  - Fast acceleration (lower `qsec`)
- Apply practical filters:
  - Cylinders
  - Transmission (Automatic/Manual)
  - Minimum mpg
- Instantly get:
  - A **Best match** car card
  - A **Top 10 ranked list** you can tap to open a zoom modal

**How FitScore is computed**
- Each feature is standardized (z-score).
- Weight and acceleration are flipped so “better” is higher (`-wt`, `-qsec`).
- Dropdown priorities map to weights: Low=1, Medium=2, High=3, Very high=4.
- Final score = weighted sum of standardized features.

---

### 📊 Insights (PCA + Clustering)
- Choose which variables to include in PCA (mpg, hp, wt, qsec, drat)
- View a **PC1 vs PC2 performance map**
- Run **k-means clustering (k = 2–6)** on PC1–PC2
- Optional car labels
- View supporting tables:
  - Explained variance (eigenvalues, proportions, cumulative)
  - Feature influence (PCA loadings)
  - Cluster profiles (avg mpg, hp, wt, qsec, cars per cluster)
- Click a point (car icon) to **zoom** into a car modal with details

---

## Dataset
- Uses the built-in R dataset: **`mtcars`**
- Adds helper fields:
  - `car` (name from rownames)
  - `transmission` (Automatic/Manual from `am`)
  - `cylinders` (factor from `cyl`)

---

## Tech stack
- **R**
- **Shiny**
- **ggplot2** (visuals)
- **dplyr** (data wrangling)
- **DT** (raw data table modal)
- **bslib** (theme + styling support)

---

## UI / UX highlights
- “Hologram / Vision Pro” glassmorphism cards
- Parallax motion layer (pure JS)
- Rotating “wheel text” feature callouts on the Home orb
- Tap-to-zoom car cards + plot click-to-zoom modal

---

## Run locally

### 1) Install packages
```r
install.packages(c("shiny", "ggplot2", "dplyr", "DT", "bslib"))
