# NASA Meteorite Landings Classification

This project investigates which characteristics are associated with whether a meteorite was **observed falling** (`Fell`) or **discovered later** (`Found`). The analysis uses the [NASA Meteorite Landings dataset](https://data.nasa.gov/docs/legacy/meteorite_landings/Meteorite_Landings.csv), compiled by The Meteoritical Society.

## Research question

How are meteorite composition, mass, year, and geographic location associated with the probability that a meteorite is classified as `Fell` rather than `Found`?

## Data

The original dataset contains more than 34,000 recorded meteorites. The analysis:

- Retains meteorites marked as valid.
- Removes observations with missing modeling variables.
- Removes implausible years and invalid geographic coordinates.
- Groups composition into stone, iron, and stony-iron categories.
- Groups mass into small, medium, and large categories.
- Divides observations into early/later years and geographic quadrants.

The cleaned sample contains approximately 31,000 observations. The raw dataset is downloaded directly from NASA when the analysis runs and is not duplicated in this repository.

## Methods

- Exploratory data analysis and proportional bar charts
- Chi-square tests of association
- Binary logistic regression
- Main-effects, reduced, and interaction models
- Stratified 70/30 training-test split
- Model comparison using AIC, ROC curves, AUC, odds ratios, and confusion matrices

## Main results

- Mass, composition, year, and geographic region were significantly associated with `Fell`/`Found` status.
- Geographic location and meteorite mass were especially informative predictors.
- The interaction model achieved an AUC of approximately **0.96** on the test data.
- The outcome was highly imbalanced: about 96% of observations were `Found` and about 4% were `Fell`.

These results describe associations in the recorded dataset. They may also reflect differences in observation, reporting, search effort, and geographic coverage rather than only physical meteorite properties.

## Repository structure

```text
.
├── analysis/
│   └── meteorite_analysis.Rmd
├── presentation/
│   └── Meteorite_Landings_Presentation.pdf
├── .gitignore
└── README.md
```

## Reproducing the analysis

1. Install R and RStudio.
2. Install the required packages:

   ```r
   install.packages(c("dplyr", "ggplot2", "caret", "pROC", "knitr", "rmarkdown"))
   ```

3. Open `analysis/meteorite_analysis.Rmd`.
4. Knit the document to HTML.

An internet connection is required the first time the NASA data is downloaded.

## Contributors

- Eno Umoren
- Camila Nunez Polanco
- Rohil Nataraj

## Data source

NASA Open Data, *Meteorite Landings*, compiled by The Meteoritical Society.
