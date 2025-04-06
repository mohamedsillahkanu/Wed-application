# **📅 Week 3: Exploratory Data Analysis (EDA) & Visualization for Malaria Data**  

This week, we will:  
✅ **Master descriptive statistics & summary tables** for malaria datasets  
✅ **Learn to handle missing values** with `na.omit()` and `tidyr::replace_na()`  
✅ **Create effective visualizations with `ggplot2`** for malaria data analysis  

---

## **1️⃣ Descriptive Statistics & Summary Tables**

### **What is Exploratory Data Analysis (EDA)?**  
📌 **EDA** is the process of analyzing data sets to summarize their main characteristics, often using visual methods. It's a critical first step before building complex models.

### **Step 1: Basic Summary Statistics**
```r
# Load our malaria dataset
malaria_data <- read.csv("malaria_dataset.csv")

# Generate basic summary statistics
summary_stats <- summary(malaria_data)
print(summary_stats)
```
### **🔍 Explanation:**  
✔ `summary()` provides basic statistics for each column: min, max, mean, median, and quartiles  
✔ For categorical variables, it shows counts of each level  

---

### **Step 2: Group-wise Statistics**
```r
# Load dplyr for data manipulation
library(dplyr)

# Calculate mean malaria cases by region
region_stats <- malaria_data %>%
  group_by(region) %>%
  summarize(
    mean_cases = mean(cases, na.rm = TRUE),
    median_cases = median(cases, na.rm = TRUE),
    min_cases = min(cases, na.rm = TRUE),
    max_cases = max(cases, na.rm = TRUE)
  )
```
### **🔍 Explanation:**  
✔ `group_by()` allows us to perform operations by group (e.g., region)  
✔ `summarize()` computes summary statistics for each group  
✔ `na.rm = TRUE` ensures we ignore missing values in our calculations  

---

### **Step 3: Frequency Tables**
```r
# Create frequency table for severity levels
severity_table <- table(malaria_data$severity)
print(severity_table)

# Calculate proportion table
severity_prop <- prop.table(severity_table) * 100
print(severity_prop)
```
### **🔍 Explanation:**  
✔ `table()` counts occurrences of each category in a variable  
✔ `prop.table()` converts counts to proportions (multiplied by 100 for percentages)  

---

### **Step 4: Cross-tabulation**
```r
# Create cross-tabulation of region and severity
region_severity_table <- table(malaria_data$region, malaria_data$severity)
print(region_severity_table)

# Calculate chi-square test for association
chisq_test <- chisq.test(region_severity_table)
print(chisq_test)
```
### **🔍 Explanation:**  
✔ Cross-tabulation shows the relationship between two categorical variables  
✔ `chisq.test()` tests whether there's a significant association between region and severity  

---

## **2️⃣ Handling Missing Values in Malaria Data**  

### **Step 1: Identifying Missing Values**
```r
# Check for missing values in the dataset
missing_values <- colSums(is.na(malaria_data))
print(missing_values)

# Calculate the percentage of missing values
missing_percentage <- colMeans(is.na(malaria_data)) * 100
print(missing_percentage)
```
### **🔍 Explanation:**  
✔ `is.na()` identifies missing values in the dataset  
✔ `colSums()` sums the missing values in each column  
✔ `colMeans()` calculates the proportion of missing values in each column  

---

### **Step 2: Removing Rows with Missing Values**
```r
# Remove rows with any missing values
complete_data <- na.omit(malaria_data)

# Check how many rows were removed
original_rows <- nrow(malaria_data)
complete_rows <- nrow(complete_data)
removed_rows <- original_rows - complete_rows
print(paste("Removed", removed_rows, "rows with missing data"))
```
### **🔍 Explanation:**  
✔ `na.omit()` removes any row that contains at least one missing value  
✔ This is a simple approach but may remove too much data if missing values are common  

---

### **Step 3: Replacing Missing Values with tidyr**
```r
# Load tidyr package
library(tidyr)

# Replace missing values in 'cases' with the mean
malaria_data_imputed <- malaria_data %>%
  mutate(cases = replace_na(cases, mean(cases, na.rm = TRUE)))

# Replace missing values in 'severity' with "Unknown"
malaria_data_imputed <- malaria_data_imputed %>%
  mutate(severity = replace_na(severity, "Unknown"))
```
### **🔍 Explanation:**  
✔ `tidyr::replace_na()` replaces NA values with specified replacements  
✔ For numeric columns, we often replace with mean, median, or zero  
✔ For categorical columns, we may replace with a new category like "Unknown"  

---

### **Step 4: Missing Value Visualization**
```r
# Install and load packages for missing data visualization
install.packages("naniar")
library(naniar)

# Create a visualization of missing data patterns
gg_miss_var(malaria_data)

# Create a matrix of missing data patterns
vis_miss(malaria_data)
```
### **🔍 Explanation:**  
✔ `naniar` package provides specialized tools for exploring missing data  
✔ `gg_miss_var()` creates a plot showing the count of missing values by variable  
✔ `vis_miss()` creates a matrix visualization of missing values throughout the dataset  

---

## **3️⃣ Data Visualization with ggplot2 for Malaria Analysis**

### **Step 1: Installing and Loading ggplot2**
```r
# Install and load ggplot2
install.packages("ggplot2")
library(ggplot2)
```
### **🔍 Explanation:**  
✔ `ggplot2` is a powerful visualization package based on the Grammar of Graphics  
✔ It creates visualizations by layering components (data, aesthetics, geometries)  

---

### **Step 2: Creating Histograms**
```r
# Create a histogram of malaria cases
ggplot(malaria_data, aes(x = cases)) +
  geom_histogram(binwidth = 50, fill = "steelblue", color = "white") +
  labs(
    title = "Distribution of Malaria Cases",
    x = "Number of Cases",
    y = "Frequency"
  ) +
  theme_minimal()
```
### **🔍 Explanation:**  
✔ `ggplot()` initializes the plot with data and aesthetic mappings  
✔ `geom_histogram()` adds a histogram layer with specified bin width  
✔ `labs()` adds titles and labels  
✔ `theme_minimal()` applies a clean, minimal theme  

---

### **Step 3: Creating Boxplots**
```r
# Create boxplots of cases by region
ggplot(malaria_data, aes(x = region, y = cases, fill = region)) +
  geom_boxplot() +
  labs(
    title = "Malaria Cases by Region",
    x = "Region",
    y = "Number of Cases"
  ) +
  theme_minimal() +
  theme(legend.position = "none") # Remove legend as it's redundant
```
### **🔍 Explanation:**  
✔ `geom_boxplot()` creates boxplots showing the distribution within each group  
✔ The boxplot shows median, quartiles, and outliers  
✔ `fill = region` colors each boxplot by region  

---

### **Step 4: Creating Bar Charts**
```r
# Create a bar chart of average cases by region
region_avg <- malaria_data %>%
  group_by(region) %>%
  summarize(avg_cases = mean(cases, na.rm = TRUE))

ggplot(region_avg, aes(x = region, y = avg_cases, fill = region)) +
  geom_col() +
  labs(
    title = "Average Malaria Cases by Region",
    x = "Region",
    y = "Average Number of Cases"
  ) +
  theme_minimal() +
  theme(legend.position = "none")
```
### **🔍 Explanation:**  
✔ `geom_col()` creates bars with heights proportional to values  
✔ First we aggregate the data, then visualize the aggregated stats  

---

### **Step 5: Time Series Line Plots**
```r
# Create a time series plot of malaria cases
ggplot(malaria_data, aes(x = date, y = cases)) +
  geom_line(color = "darkred") +
  geom_point(color = "darkred") +
  labs(
    title = "Malaria Cases Over Time",
    x = "Date",
    y = "Number of Cases"
  ) +
  theme_minimal() +
  scale_x_date(date_breaks = "1 month", date_labels = "%b %Y")
```
### **🔍 Explanation:**  
✔ `geom_line()` connects points with lines to show trends over time  
✔ `geom_point()` adds points at each observation  
✔ `scale_x_date()` formats the x-axis for date data  

---

### **Step 6: Faceted Plots**
```r
# Create faceted plots by region
ggplot(malaria_data, aes(x = date, y = cases)) +
  geom_line() +
  geom_point() +
  facet_wrap(~region, scales = "free_y") +
  labs(
    title = "Malaria Cases Over Time by Region",
    x = "Date",
    y = "Number of Cases"
  ) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```
### **🔍 Explanation:**  
✔ `facet_wrap()` creates separate panels for each region  
✔ `scales = "free_y"` allows each panel to have its own y-axis scale  
✔ The angled x-axis text improves readability when dates are displayed  

---

## **✅ Summary of Week 3**  
By the end of this week, you should:  
✔ **Know how to generate descriptive statistics** for malaria data  
✔ **Understand methods for handling missing values** in datasets  
✔ **Be able to create effective visualizations** using ggplot2  
✔ **Interpret visual patterns** to identify trends in malaria data  

--- 

# **📌 Week 3: Exercises – Exploratory Data Analysis & Visualization for Malaria Data**  

This week's exercises will focus on applying descriptive statistics, handling missing values, and creating insightful visualizations of malaria data. These skills are critical for understanding your data before proceeding to more complex analyses.

---

## **1️⃣ Descriptive Statistics & Summary Tables**  

### **Exercise 1.1: Basic Summary Statistics**  
🔹 **You have a dataset called `malaria_surveillance` with the following columns:**  
- `district`: Name of the district  
- `month`: Month of data collection (1-12)  
- `year`: Year of data collection  
- `cases`: Number of reported malaria cases  
- `deaths`: Number of malaria-related deaths  
- `population`: Population of the district  

**Write the R code to:**  
1. Load the dataset and display its structure using `str()`.  
2. Calculate summary statistics for all numeric variables.  
3. Find the district with the highest number of cases.  
4. Calculate the case fatality rate (deaths/cases) for each district.  

---

### **Exercise 1.2: Group-wise Statistics**  
🔹 **Using the same dataset, analyze malaria statistics by district and year.**  

**Write the R code to:**  
1. Calculate the average number of cases per year for each district.  
2. Identify the year with the highest total number of cases across all districts.  
3. Calculate the incidence rate (cases per 1000 population) for each district-year combination.  
4. Create a summary table showing the top 5 district-year combinations with the highest incidence rates.  

---

### **Exercise 1.3: Statistical Tests**  
🔹 **Perform statistical comparisons between different groups in the dataset.**  

**Write the R code to:**  
1. Test whether there is a significant difference in mean cases between districts using ANOVA.  
2. Perform a t-test to compare cases between two specific districts of your choice.  
3. Check if there's a correlation between population size and number of cases using Pearson's correlation.  

---

## **2️⃣ Handling Missing Values**  

### **Exercise 2.1: Identify Missing Data**  
🔹 **The `malaria_surveillance` dataset has some missing values in the `cases` and `deaths` columns.**  

**Write the R code to:**  
1. Count how many values are missing in each column.  
2. Calculate the percentage of missing values in each column.  
3. Identify districts with the most missing values.  

---

### **Exercise 2.2: Handle Missing Values**  
🔹 **Apply different strategies to handle missing data in the dataset.**  

**Write the R code to:**  
1. Create a new dataset with complete cases only (no missing values).  
2. Create another dataset where missing `cases` values are replaced with the mean of the district.  
3. For missing `deaths` values, replace with 0 and create a new flag column called `deaths_imputed` that is TRUE when the value was imputed.  

---

### **Exercise 2.3: Missing Data Visualization**  
🔹 **Visualize the patterns of missing data in the dataset.**  

**Write the R code to:**  
1. Create a visualization showing the proportion of missing values in each column.  
2. Visualize how missing values are distributed across districts.  
3. Create a heatmap showing where missing values occur in the dataset.  

---

## **3️⃣ Data Visualization with ggplot2**  

### **Exercise 3.1: Temporal Trends**  
🔹 **Visualize how malaria cases change over time.**  

**Write the R code to:**  
1. Create a line plot showing the total cases per month across all years.  
2. Make a faceted plot showing yearly trends, with one panel per year.  
3. Create a heatmap where x-axis is month, y-axis is year, and color represents number of cases.  

---

### **Exercise 3.2: Spatial Comparison**  
🔹 **Compare malaria statistics across different districts.**  

**Write the R code to:**  
1. Create a bar chart showing the total cases by district in descending order.  
2. Make boxplots comparing the distribution of monthly cases across districts.  
3. Create a scatter plot with population on the x-axis and average cases on the y-axis, with points colored by district.  

---

### **Exercise 3.3: Relationship Visualization**  
🔹 **Explore relationships between variables in the dataset.**  

**Write the R code to:**  
1. Create a scatter plot showing the relationship between cases and deaths, with a trend line.  
2. Make a bubble chart where x-axis is population, y-axis is cases, and bubble size represents deaths.  
3. Create a correlation plot showing relationships between all numeric variables.  

---

## **4️⃣ Bonus Challenge: Dashboard Creation**  

🔹 **Create a simple dashboard using R Markdown and flexdashboard to display key malaria statistics and visualizations.**  

**Write the R code to:**  
1. Create a flexdashboard with at least 3 panels.  
2. Include summary statistics, a time series plot, and a comparison across districts.  
3. Add interactive elements with plotly (if you're familiar with it).  
4. Make the dashboard self-contained so it can be shared with others.  

📌 **Hint:** Use `install.packages("flexdashboard")` and check the flexdashboard documentation for templates.

---

Here are the **solutions** for **Week 3: Exploratory Data Analysis & Visualization for Malaria Data**:

---

## **1️⃣ Descriptive Statistics & Summary Tables**

### **Exercise 1.1: Basic Summary Statistics**  
```r
# Load the dataset
malaria_surveillance <- read.csv("malaria_surveillance.csv")

# Display the structure of the dataset
str(malaria_surveillance)

# Calculate summary statistics for all numeric variables
summary(malaria_surveillance[, c("cases", "deaths", "population")])

# Find the district with the highest number of cases
max_cases_district <- malaria_surveillance[which.max(malaria_surveillance$cases), "district"]
max_cases <- max(malaria_surveillance$cases, na.rm = TRUE)
cat("District with highest cases:", max_cases_district, "with", max_cases, "cases\n")

# Calculate the case fatality rate for each district
library(dplyr)
cfr_by_district <- malaria_surveillance %>%
  group_by(district) %>%
  summarize(
    total_cases = sum(cases, na.rm = TRUE),
    total_deaths = sum(deaths, na.rm = TRUE),
    cfr = (total_deaths / total_cases) * 100
  ) %>%
  arrange(desc(cfr))

print(cfr_by_district)
```

**Explanation:**
- `str()` shows the structure of the dataset including variable types.
- `summary()` provides basic statistics for the selected numeric columns.
- `which.max()` finds the row with the maximum value in the cases column.
- We calculate the case fatality rate (CFR) as (deaths/cases)*100 for each district.

---

### **Exercise 1.2: Group-wise Statistics**  
```r
# Calculate average cases per year for each district
avg_cases_by_district_year <- malaria_surveillance %>%
  group_by(district, year) %>%
  summarize(avg_cases = mean(cases, na.rm = TRUE)) %>%
  arrange(district, year)

print(avg_cases_by_district_year)

# Identify the year with highest total cases
yearly_totals <- malaria_surveillance %>%
  group_by(year) %>%
  summarize(total_cases = sum(cases, na.rm = TRUE)) %>%
  arrange(desc(total_cases))

cat("Year with highest total cases:", yearly_totals$year[1], 
    "with", yearly_totals$total_cases[1], "cases\n")

# Calculate incidence rate per 1000 population
incidence_by_district_year <- malaria_surveillance %>%
  group_by(district, year) %>%
  summarize(
    total_cases = sum(cases, na.rm = TRUE),
    avg_population = mean(population, na.rm = TRUE),
    incidence_per_1000 = (total_cases / avg_population) * 1000
  ) %>%
  arrange(desc(incidence_per_1000))

# Top 5 district-year combinations with highest incidence
top_5_incidence <- head(incidence_by_district_year, 5)
print(top_5_incidence)
```

**Explanation:**
- We group the data by district and year to calculate average cases.
- For yearly totals, we group only by year and sum all cases.
- Incidence rate is calculated as (cases/population)*1000 for standardization.
- `head()` selects the top 5 rows after sorting by incidence rate.

---

### **Exercise 1.3: Statistical Tests**  
```r
# ANOVA to test for difference in mean cases between districts
cases_anova <- aov(cases ~ district, data = malaria_surveillance)
summary(cases_anova)

# T-test to compare cases between two specific districts
district_a <- "Central"  # Replace with actual district name
district_b <- "Eastern"  # Replace with actual district name

t_test_result <- t.test(
  malaria_surveillance$cases[malaria_surveillance$district == district_a],
  malaria_surveillance$cases[malaria_surveillance$district == district_b]
)
print(t_test_result)

# Check correlation between population size and number of cases
correlation <- cor.test(
  malaria_surveillance$population, 
  malaria_surveillance$cases,
  method = "pearson"
)
print(correlation)
```

**Explanation:**
- ANOVA tests whether there are significant differences in means across multiple groups.
- The t-test compares means between two specific groups.
- Pearson's correlation measures the linear relationship between population and cases.

---

## **2️⃣ Handling Missing Values**

### **Exercise 2.1: Identify Missing Data**  
```r
# Count missing values in each column
missing_count <- colSums(is.na(malaria_surveillance))
print(missing_count)

# Calculate percentage of missing values
missing_percentage <- colMeans(is.na(malaria_surveillance)) * 100
print(missing_percentage)

# Identify districts with most missing values
missing_by_district <- malaria_surveillance %>%
  group_by(district) %>%
  summarize(
    missing_cases = sum(is.na(cases)),
    missing_deaths = sum(is.na(deaths)),
    total_missing = missing_cases + missing_deaths
  ) %>%
  arrange(desc(total_missing))

print(missing_by_district)
```

**Explanation:**
- `colSums(is.na())` counts missing values in each column.
- `colMeans(is.na()) * 100` calculates the percentage of missing values.
- We group by district to identify which districts have the most missing data.

---

### **Exercise 2.2: Handle Missing Values**  
```r
# Dataset with complete cases only
complete_data <- na.omit(malaria_surveillance)
cat("Original rows:", nrow(malaria_surveillance), 
    "Complete rows:", nrow(complete_data), 
    "Removed:", nrow(malaria_surveillance) - nrow(complete_data), "\n")

# Replace missing cases with district mean
imputed_cases <- malaria_surveillance %>%
  group_by(district) %>%
  mutate(cases = ifelse(is.na(cases), 
                         mean(cases, na.rm = TRUE), 
                         cases))

# Replace missing deaths with 0 and create flag
imputed_deaths <- malaria_surveillance %>%
  mutate(
    deaths_imputed = is.na(deaths),
    deaths = ifelse(is.na(deaths), 0, deaths)
  )

# Check the results
summary(imputed_cases$cases)
summary(imputed_deaths$deaths)
table(imputed_deaths$deaths_imputed)
```

**Explanation:**
- `na.omit()` removes rows with any missing values.
- For imputing missing cases, we use the mean of each district.
- For missing deaths, we replace with 0 and create a flag to track which values were imputed.

---

### **Exercise 2.3: Missing Data Visualization**  
```r
# Visualize proportion of missing values by column
library(naniar)  # Install if needed: install.packages("naniar")

gg_miss_var(malaria_surveillance)

# Visualize missing values by district
gg_miss_var(malaria_surveillance, facet = district)

# Create a heatmap of missing values
vis_miss(malaria_surveillance)
```

**Explanation:**
- `gg_miss_var()` creates a bar chart showing missing values by variable.
- By adding `facet = district`, we can see missing value patterns by district.
- `vis_miss()` creates a heatmap where cells are colored by whether they are missing or not.

---

## **3️⃣ Data Visualization with ggplot2**

### **Exercise 3.1: Temporal Trends**  
```r
library(ggplot2)
library(lubridate)

# Create a date variable for proper time series plotting
malaria_surveillance <- malaria_surveillance %>%
  mutate(date = make_date(year, month, 1))

# Line plot showing total cases per month across all years
monthly_cases <- malaria_surveillance %>%
  group_by(month) %>%
  summarize(total_cases = sum(cases, na.rm = TRUE))

ggplot(monthly_cases, aes(x = month, y = total_cases, group = 1)) +
  geom_line() +
  geom_point() +
  scale_x_continuous(breaks = 1:12) +
  labs(
    title = "Total Malaria Cases by Month",
    x = "Month",
    y = "Total Cases"
  ) +
  theme_minimal()

# Faceted plot showing yearly trends
yearly_trends <- malaria_surveillance %>%
  group_by(year, month) %>%
  summarize(total_cases = sum(cases, na.rm = TRUE))

ggplot(yearly_trends, aes(x = month, y = total_cases, group = 1)) +
  geom_line() +
  geom_point() +
  facet_wrap(~year) +
  scale_x_continuous(breaks = c(1, 4, 7, 10)) +
  labs(
    title = "Monthly Malaria Cases by Year",
    x = "Month",
    y = "Total Cases"
  ) +
  theme_minimal()

# Heatmap of cases by month and year
ggplot(yearly_trends, aes(x = month, y = factor(year), fill = total_cases)) +
  geom_tile() +
  scale_fill_gradient(low = "white", high = "red") +
  scale_x_continuous(breaks = 1:12) +
  labs(
    title = "Heatmap of Malaria Cases",
    x = "Month",
    y = "Year",
    fill = "Cases"
  ) +
  theme_minimal()
```

**Explanation:**
- We create a proper date variable for time series analysis.
- The first plot shows the seasonal pattern across all years.
- The faceted plot shows yearly trends with separate panels.
- The heatmap provides a color-coded view of cases by month and year.

---

### **Exercise 3.2: Spatial Comparison**  
```r
# Bar chart of total cases by district
district_totals <- malaria_surveillance %>%
  group_by(district) %>%
  summarize(total_cases = sum(cases, na.rm = TRUE)) %>%
  arrange(desc(total_cases))

ggplot(district_totals, aes(x = reorder(district, -total_cases), y = total_cases)) +
  geom_col(fill = "steelblue") +
  labs(
    title = "Total Malaria Cases by District",
    x = "District",
    y = "Total Cases"
  ) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))

# Boxplots comparing monthly cases across districts
ggplot(malaria_surveillance, aes(x = district, y = cases)) +
  geom_boxplot(fill = "lightgreen") +
  labs(
    title = "Distribution of Monthly Malaria Cases by District",
    x = "District",
    y = "Cases"
  ) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))

# Scatter plot of population vs. average cases
district_avg <- malaria_surveillance %>%
  group_by(district) %>%
  summarize(
    avg_cases = mean(cases, na.rm = TRUE),
    avg_population = mean(population, na.rm = TRUE)
  )

ggplot(district_avg, aes(x = avg_population, y = avg_cases, color = district)) +
  geom_point(size = 3) +
  labs(
    title = "Average Cases vs. Population by District",
    x = "Average Population",
    y = "Average Cases"
  ) +
  theme_minimal()
```

**Explanation:**
- The bar chart shows total cases by district in descending order.
- Boxplots display the distribution of cases within each district.
- The scatter plot reveals the relationship between population size and average cases.

---

### **Exercise 3.3: Relationship Visualization**  
```r
# Scatter plot of cases vs deaths with trend line
ggplot(malaria_surveillance, aes(x = cases, y = deaths)) +
  geom_point(alpha = 0.5) +
  geom_smooth(method = "lm", color = "red") +
  labs(
    title = "Relationship Between Malaria Cases and Deaths",
    x = "Number of Cases",
    y = "Number of Deaths"
  ) +
  theme_minimal()

# Bubble chart
ggplot(malaria_surveillance, aes(x = population, y = cases, size = deaths)) +
  geom_point(alpha = 0.6, color = "purple") +
  scale_size_continuous(range = c(1, 10)) +
  labs(
    title = "Malaria Cases by Population and Deaths",
    x = "Population",
    y = "Cases",
    size = "Deaths"
  ) +
  theme_minimal()

# Correlation plot
library(corrplot)
numeric_vars <- malaria_surveillance[, c("cases", "deaths", "population")]
correlation_matrix <- cor(numeric_vars, use = "complete.obs")
corrplot(correlation_matrix, method = "circle")
```

**Explanation:**
- The scatter plot with trend line shows the relationship between cases and deaths.
- The bubble chart visualizes three variables: population, cases, and deaths.
- The correlation plot shows the strength of relationships between all numeric variables.

---

### **Step 7: Advanced Visualization with Interactive Elements**
```r
# Install and load packages for interactive plots
install.packages("plotly")
library(plotly)

# Convert ggplot to interactive plot with plotly
cases_by_district <- ggplot(district_totals, aes(x = reorder(district, -total_cases), 
                                               y = total_cases,
                                               text = paste("District:", district, 
                                                           "<br>Cases:", total_cases))) +
  geom_col(fill = "steelblue") +
  labs(title = "Total Malaria Cases by District", x = "District", y = "Total Cases") +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))

# Convert to interactive plot
interactive_plot <- ggplotly(cases_by_district, tooltip = "text")
interactive_plot
```
### **🔍 Explanation:**  
✔ `plotly` converts static ggplot2 visualizations to interactive plots  
✔ Interactive elements include tooltips, zooming, and panning  
✔ The `tooltip` parameter controls what information appears when hovering  

---

## **4️⃣ Bonus Challenge: Dashboard Creation**  

```r
# This is sample code for creating a flexdashboard
# Save this to an R Markdown file with YAML header:

# ---
# title: "Malaria Surveillance Dashboard"
# output: 
#   flexdashboard::flex_dashboard:
#     orientation: rows
#     social: menu
#     source_code: embed
# ---
# 
# ```{r setup, include=FALSE}
# library(flexdashboard)
# library(tidyverse)
# library(plotly)
# library(DT)
# 
# # Load data
# malaria_surveillance <- read.csv("malaria_surveillance.csv")
# ```
# 
# Overview
# =====================================
# 
# Row {data-height=150}
# -------------------------------------
# 
# ### Total Cases
# ```{r}
# valueBox(
#   sum(malaria_surveillance$cases, na.rm = TRUE),
#   icon = "fa-user-md",
#   color = "primary"
# )
# ```
# 
# ### Total Deaths
# ```{r}
# valueBox(
#   sum(malaria_surveillance$deaths, na.rm = TRUE),
#   icon = "fa-heartbeat",
#   color = "danger"
# )
# ```
# 
# ### Average Case Fatality Rate
# ```{r}
# cfr <- sum(malaria_surveillance$deaths, na.rm = TRUE) / 
#       sum(malaria_surveillance$cases, na.rm = TRUE) * 100
# 
# valueBox(
#   paste0(round(cfr, 2), "%"),
#   icon = "fa-percent",
#   color = "warning"
# )
# ```
# 
# Row
# -------------------------------------
# 
# ### Malaria Cases Over Time
# ```{r}
# time_series <- malaria_surveillance %>%
#   group_by(year, month) %>%
#   summarize(total_cases = sum(cases, na.rm = TRUE)) %>%
#   mutate(date = as.Date(paste(year, month, "01", sep = "-")))
# 
# plot_ly(time_series, x = ~date, y = ~total_cases, type = "scatter", mode = "lines+markers") %>%
#   layout(title = "Malaria Cases Over Time",
#          xaxis = list(title = "Date"),
#          yaxis = list(title = "Total Cases"))
# ```
# 
# Row
# -------------------------------------
# 
# ### Cases by District
# ```{r}
# district_data <- malaria_surveillance %>%
#   group_by(district) %>%
#   summarize(total_cases = sum(cases, na.rm = TRUE)) %>%
#   arrange(desc(total_cases))
# 
# plot_ly(district_data, x = ~reorder(district, total_cases), y = ~total_cases, type = "bar", marker = list(color = "steelblue")) %>%
#   layout(title = "Total Cases by District",
#          xaxis = list(title = "District"),
#          yaxis = list(title = "Total Cases"))
# ```
# 
# District Details
# =====================================
# 
# ### District Comparison Table
# ```{r}
# district_summary <- malaria_surveillance %>%
#   group_by(district) %>%
#   summarize(
#     total_cases = sum(cases, na.rm = TRUE),
#     total_deaths = sum(deaths, na.rm = TRUE),
#     avg_population = mean(population, na.rm = TRUE),
#     cfr = round((total_deaths / total_cases * 100), 2),
#     incidence_per_1000 = round((total_cases / avg_population * 1000), 2)
#   ) %>%
#   arrange(desc(total_cases))
# 
# datatable(district_summary, 
#           options = list(pageLength = 10),
#           rownames = FALSE)
# ```
# 
# Temporal Patterns
# =====================================
# 
# ### Monthly Pattern
# ```{r}
# monthly_pattern <- malaria_surveillance %>%
#   group_by(month) %>%
#   summarize(avg_cases = mean(cases, na.rm = TRUE)) %>%
#   mutate(month_name = month.name[month])
# 
# plot_ly(monthly_pattern, x = ~month_name, y = ~avg_cases, type = "bar", marker = list(color = "darkgreen")) %>%
#   layout(title = "Average Cases by Month",
#          xaxis = list(title = "Month"),
#          yaxis = list(title = "Average Cases"))
# ```
