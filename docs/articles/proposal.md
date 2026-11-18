# BST260 Final Project Proposal

**To: BST260 Teaching Team, Fall 2026**

## Project Overview

The objective of this project is to investigate two distinct public
health questions using publicly available datasets. The project will
apply data management, visualization, regression modeling, and model
assessment techniques introduced in BST260. Particular attention will be
given to data provenance, statistical uncertainty, model assumptions,
and limitations of scientific interpretation.

## Vignette 1: Association Between Body Mass Index and Systolic Blood Pressure Among U.S. Adults

### Data Source and Study Population

The first analysis will use data from the National Health and Nutrition
Examination Survey (NHANES), available through the NHANES R package. The
dataset contains 10,000 observations and 77 variables from the 2009–2010
and 2011–2012 survey cycles.

The study will focus on adults aged 20 years or older. Preliminary data
exploration identified 7,235 eligible observations corresponding to
4,654 unique participant IDs.

### Research Question

Is body mass index associated with systolic blood pressure among adults,
after accounting for demographic and lifestyle characteristics? Does
this association depart from a linear relationship?

### Variables and Unit of Analysis

The primary exposure will be body mass index (BMI), measured in kg/m²
and treated as a continuous variable. The primary outcome will be
average systolic blood pressure (BPSysAve), measured in mmHg.

Age, gender, race and ethnicity, physical activity, and smoking history
will be considered potential confounding or adjustment variables based
on their plausible relationships with BMI and blood pressure.

The underlying unit of analysis is the individual participant. Repeated
participant IDs resulting from the resampling procedure used to
construct the NHANES teaching dataset will be explicitly considered.

### Statistical Analysis Plan

The analysis will begin with descriptive statistics and exploratory
visualization of BMI, systolic blood pressure, and relevant covariates.

Simple and multiple linear regression models will be fitted to
investigate the association between BMI and systolic blood pressure
before and after covariate adjustment. Natural cubic splines will be
used to examine potential nonlinear relationships.

Model comparison, residual diagnostics, confidence intervals, and
appropriate statistical tests will be used to evaluate model fit and
uncertainty. The implications of repeated participant IDs will be
addressed through appropriate sensitivity analyses, potentially
including participant-clustered standard errors or survey-weighted
analysis using NHANESraw.

### Missing Data and Limitations

Among the eligible adult observations, BMI has 63 missing values (0.87%)
and systolic blood pressure has 264 missing values (3.65%). The selected
adjustment variables have no missing values in this subset.

Complete-case analysis will serve as the initial approach, with an
assessment of potential differences between included and excluded
observations.

Important limitations include the cross-sectional study design, residual
confounding, measurement variability, repeated participant IDs, and
limitations associated with the resampled teaching dataset. The
estimated relationships will be interpreted as associations rather than
causal effects.

## Vignette 2: Temporal and Geographic Patterns of Waterborne Disease Outbreaks

### Data Source and Study Population

The second analysis will use CDC outbreak surveillance data provided as
the waterborne dataset in the finalproject R package.

The original dataset contains 66,713 outbreak records and 23 variables
after conversion from a nested list into a tabular format. Restricting
the dataset to records with water as the primary mode of transmission
yields 3,106 records spanning 1971–2023, with no duplicated record
identifiers.

The study will focus on reported waterborne disease outbreaks in the
United States and will explicitly document the treatment of territorial
and multistate records.

### Research Question

How do reported waterborne disease outbreaks vary by month, calendar
year, and geographic location? Do seasonal patterns differ across major
categories of water exposure?

### Variables and Unit of Analysis

The primary outcome will be the number of reported waterborne outbreaks
aggregated within calendar months.

The primary explanatory variables will be month and year. Month will be
treated as a categorical variable to examine seasonality, while year
will be used to investigate long-term temporal trends.

Geographic location and water exposure category will be examined in
secondary analyses. Categories will be defined consistently, with
explicit handling of records involving multiple or undetermined exposure
types.

The original unit of observation is an outbreak record, while the
primary regression analysis will use aggregated year-month outbreak
counts.

### Statistical Analysis Plan

Descriptive statistics and graphical summaries will be used to
characterize seasonal patterns, annual trends, geographic variation, and
outbreak characteristics.

Poisson regression will be used to model monthly outbreak counts. The
model will incorporate calendar month and year, with consideration of
differences in month length and reporting coverage. Overdispersion will
be assessed, and negative binomial regression will be considered if the
Poisson variance assumption is inadequate.

Residual diagnostics, model comparison, and confidence intervals will be
used to assess model performance. Potential temporal dependence and
changes in surveillance practices will also be investigated.

Additional exploratory analyses will examine differences between
drinking-water and recreational-water outbreaks. Outbreak size will be
summarized using robust descriptive statistics because the preliminary
distribution of reported illnesses is highly right-skewed.

### Missing Data and Limitations

The filtered dataset contains no missing values for year, month, state,
or the number of reported illnesses. Missing information in secondary
variables, including deaths and water type, will be documented and
handled explicitly.

Reporting coverage will be examined before constructing zero-count
periods. Periods with unknown reporting status will not automatically be
interpreted as periods without outbreaks.

Potential limitations include underreporting, changes in surveillance
systems, geographic differences in reporting practices, and the absence
of population or water-exposure denominators. Therefore, the analysis
will focus on reported outbreak counts rather than population-level
disease incidence or causal conclusions.

## Expected Deliverables

The final project will consist of a functional R package and a publicly
accessible pkgdown website containing two reproducible analytical
vignettes.

Each vignette will provide documentation of data provenance, clearly
defined research objectives, descriptive statistics, visualizations,
statistical modeling, scientific interpretation, and a discussion of
uncertainty and limitations.

All analyses will be implemented in R, with reproducible code and
documented data-processing decisions.

## Data Sources

- [NHANES R Package](https://cran.r-project.org/package=NHANES)
- [CDC National Health and Nutrition Examination
  Survey](https://www.cdc.gov/nchs/nhanes/)
- [CDC National Outbreak Reporting System](https://www.cdc.gov/nors/)
- [BST260 Project
  Template](https://vjcitn.github.io/bst260project-template/)
