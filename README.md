# PR. 2 Derivable Judgement

# Inferential Statistics and Hypothesis Testing

## Project Overview
This project is a Jupyter Notebook assignment on **inferential statistics and statistical hypothesis testing**. It combines short theoretical explanations with practical Python analysis of a diabetes-related dataset.

The notebook introduces core statistical concepts and applies several tests to explore relationships between variables such as age, body mass index (BMI), smoking status, and diabetes status.

## Table of Contents
- [Objectives](#objectives)
- [Concepts Covered](#concepts-covered)
- [Practical Analysis](#practical-analysis)
- [Technologies and Libraries](#technologies-and-libraries)
- [Dataset Requirements](#dataset-requirements)
- [Installation](#installation)
- [How to Run the Notebook](#how-to-run-the-notebook)
- [Expected Outputs](#expected-outputs)
- [Interpreting Results](#interpreting-results)
- [Important Notes](#important-notes)
- [Future Improvements](#future-improvements)
- [Author](#author)

## Objectives
- Understand the purpose of inferential statistics.
- Learn the components of hypothesis testing.
- Calculate confidence intervals, critical values, and p-values.
- Apply statistical tests to numerical and categorical data.
- Explore covariance and correlation between continuous variables.
- Visualize the relationship between age and BMI.
- Export the dataset to a CSV file from the notebook.

## Concepts Covered
The theoretical section explains the following topics:

### 1. Inferential Statistics
Using sample data to draw conclusions about a larger population, estimate population parameters, make predictions, and test assumptions.

### 2. Hypothesis Testing
The process of evaluating a claim about a population using a null hypothesis (`H₀`), alternative hypothesis (`H₁`), significance level (`α`), test statistic, p-value, and conclusion.

### 3. Confidence Intervals and Critical Values
A confidence interval gives a range of plausible values for a population parameter at a chosen confidence level. A critical value is a threshold used in statistical decisions.

### 4. P-value
The p-value measures how unusual the observed result, or a more extreme result, would be if the null hypothesis were true. The notebook commonly compares p-values with a significance level of `0.05`.

### 5. Type I and Type II Errors
- **Type I error:** Rejecting a null hypothesis that is actually true (false positive).
- **Type II error:** Failing to reject a null hypothesis that is actually false (false negative).

### 6. Statistical Tests
- **Z-test:** Used for mean or proportion testing when the assumptions for a normal-based test are appropriate.
- **T-test:** Used to compare means, especially when the population standard deviation is unknown.
- **Chi-square test:** Used to assess associations between categorical variables or differences between observed and expected frequencies.
- **ANOVA:** Used to compare means across three or more groups.

### 7. Covariance
Describes how two variables vary together. Its sign indicates whether they tend to move in the same or opposite directions.

### 8. Correlation
Describes the strength and direction of a linear relationship. The correlation coefficient ranges from `-1` to `+1`.

## Practical Analysis
The notebook imports NumPy, pandas, SciPy statistics, and Matplotlib, then performs the following analyses:

1. **Hypothesis test for age and diabetes status**  
   Compares the ages of records with diabetes and records without diabetes using an independent-samples Welch's t-test.

2. **Confidence interval for age**  
   Calculates the mean age, standard error, critical t-value, margin of error, and a 95% confidence interval for mean age.

3. **BMI comparison by smoking status**  
   Compares BMI values for the `Smoker` and `Non-Smoker` groups using an independent-samples t-test.

4. **Z-statistic for BMI**  
   Compares the sample BMI mean with a reference mean of `25`, using a specified population standard deviation of `4`.

5. **Chi-square test**  
   Creates a contingency table for `smoking_status` and `diabetes`, then calculates the chi-square statistic, degrees of freedom, and p-value.

6. **One-way ANOVA**  
   Compares BMI values across groups defined by `smoking_status` and reports the F-statistic and p-value.

7. **Covariance and correlation**  
   Calculates covariance and correlation matrices for `age` and `bmi`.

8. **Visualization and export**  
   Creates a scatter plot of age against BMI and saves the dataframe to `derivable_judgement_dataset.csv`.

## Technologies and Libraries
- **Python** — programming language
- **Jupyter Notebook** — interactive notebook environment
- **NumPy** — numerical operations
- **pandas** — data loading and manipulation
- **SciPy** — statistical tests and probability distributions
- **Matplotlib** — scatter-plot visualization

## Dataset Requirements
The notebook expects a CSV dataset with columns including:
- `age` — age values
- `bmi` — body mass index values
- `diabetes` — diabetes status, expected to be Boolean for the current filtering expressions
- `smoking_status` — smoking category, with values such as `Smoker` and `Non-Smoker`

The original notebook loads the dataset from a local Windows path:

```python
DF = pd.read_csv(r"D:\OneDrive\Desktop\Statistics RnW\PR. 2\Derivable Judgement.csv")
```

This path will not work on most other computers. Place the CSV file in the notebook folder and update the code to use a relative path, for example:

```python
DF = pd.read_csv("Derivable Judgement.csv")
```

Make sure the filename and column names match the actual dataset. The dataset itself is not included by this README; add it to your repository if you are permitted to share it.

## Installation

### 1. Install Python
Install a supported Python version and ensure that `python` and `pip` are available from your terminal.

### 2. Install the required packages
Run:

```bash
pip install numpy pandas scipy matplotlib jupyter
```

### 3. Get the notebook
Clone your repository or download the `.ipynb` file and required CSV dataset into your working directory.

## How to Run the Notebook
1. Open a terminal in the project folder.
2. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

3. Open the notebook file in the browser.
4. Update the dataset path in the CSV-loading cell.
5. Confirm that the expected columns are present and that `diabetes` has a compatible Boolean data type.
6. Run the cells from top to bottom.
7. Review the printed test statistics, p-values, confidence interval, covariance/correlation matrices, and scatter plot.
8. Check that the final cell creates `derivable_judgement_dataset.csv`.

## Expected Outputs
When the notebook runs successfully, it should produce:
- A preview of the loaded dataset
- Test statistics and p-values for the t-tests
- A 95% confidence interval for mean age
- A z-statistic and p-value for the BMI reference comparison
- A contingency table and chi-square test results
- ANOVA results for BMI grouped by smoking status
- Covariance and correlation matrices for age and BMI
- A scatter plot titled **Correlation between Age and BMI**
- A CSV export named `derivable_judgement_dataset.csv`

Exact numeric results depend on the input dataset and its contents.

## Interpreting Results
The notebook uses `0.05` as a common significance threshold. In general:
- If `p-value < 0.05`, reject the null hypothesis for the test being performed.
- If `p-value >= 0.05`, fail to reject the null hypothesis.

A p-value does not measure the size or practical importance of an effect, and statistical association alone does not prove causation. Check that each test's assumptions are appropriate before drawing conclusions.

## Important Notes
- The notebook uses `DF["diabetes"]` and `~DF["diabetes"]`; this expects Boolean values or a compatible Boolean series.
- The BMI z-test assumes a reference mean of `25` and population standard deviation of `4`. Confirm these values are appropriate for the assignment and dataset.
- The ANOVA code groups BMI by `smoking_status`, although its markdown prompt mentions age groups and disease rate. The README describes what the code actually performs.
- The notebook includes a diabetes-age t-test and a smoking-status/BMI t-test. These test differences in means; they do not by themselves establish that smoking causes diabetes.
- The saved CSV is written to the current working directory.
- No exact test outcomes are listed here because they depend on running the notebook with the intended dataset.

## Future Improvements
- Replace the machine-specific dataset path with a relative path.
- Add a `requirements.txt` file to document dependencies.
- Add data validation for missing values, unexpected categories, and incorrect data types.
- Ensure all hypothesis statements align with the statistical tests being performed.
- Add clear, test-specific conclusions for every hypothesis.
- Consider checking statistical assumptions and reporting effect sizes alongside p-values.
- Add a project folder structure and sample dataset if sharing is permitted.

## Author
**KANISH SINGH**
