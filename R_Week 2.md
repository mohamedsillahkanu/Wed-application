# **📅 Week 2: Data Structures & Basic Operations for Malaria Data Analysis**  

This week, we will:  
✅ **Explore basic data structures**: Vectors, matrices, lists, and data frames  
✅ **Learn indexing and subsetting** for malaria data  
✅ **Use basic functions**: `mean()`, `sum()`, `table()`, `summary()`  
✅ **Clean data with `dplyr`**: `filter()`, `select()`, `mutate()`  

---

## **1️⃣ Vectors, Matrices, Lists, and Data Frames**

### **What are Data Structures?**  
📌 **Data structures** are how data is organized and stored in R. Understanding these is key to effective data analysis.

### **Step 1: Vectors**
```r
# Creating a vector of malaria cases per region
cases_per_region <- c(150, 200, 250, 300)
```
### **🔍 Explanation:**  
✔ `c()` creates a **vector**—a basic data structure in R  
✔ `cases_per_region` stores the number of malaria cases in four different regions

---

### **Step 2: Matrices**
```r
# Creating a matrix of malaria cases (rows = regions, columns = years)
malaria_matrix <- matrix(c(150, 200, 250, 300, 120, 180, 220, 260), nrow = 2, ncol = 4)
```
### **🔍 Explanation:**  
✔ `matrix()` creates a **matrix** with a specified number of rows (`nrow`) and columns (`ncol`)  
✔ `malaria_matrix` holds the malaria case data in a 2x4 format  

---

### **Step 3: Lists**
```r
# Creating a list of malaria data
malaria_list <- list(cases_per_region, malaria_matrix, region = "West")
```
### **🔍 Explanation:**  
✔ `list()` creates a **list**, which can store multiple types of data (vectors, matrices, etc.)  
✔ `malaria_list` contains both the vector, matrix, and a text string "West"  

---

### **Step 4: Data Frames**
```r
# Creating a data frame for malaria cases per region
malaria_df <- data.frame(region = c("West", "East", "North", "South"), cases = cases_per_region)
```
### **🔍 Explanation:**  
✔ `data.frame()` creates a **data frame**, which is used to store tabular data  
✔ `malaria_df` is a data frame where `region` is a column of text and `cases` is a column of numbers  

---

## **2️⃣ Indexing & Subsetting Malaria Data**  

### **Step 1: Accessing Data in Vectors**
```r
# Accessing the first value in the vector
cases_per_region[1]
```
### **🔍 Explanation:**  
✔ `cases_per_region[1]` accesses the **first element** of the vector  

---

### **Step 2: Accessing Data in Matrices**
```r
# Accessing the element in the 1st row and 2nd column
malaria_matrix[1, 2]
```
### **🔍 Explanation:**  
✔ `malaria_matrix[1, 2]` accesses the element in the **1st row and 2nd column** of the matrix  

---

### **Step 3: Accessing Data in Data Frames**
```r
# Accessing the 'cases' column
malaria_df$cases
```
### **🔍 Explanation:**  
✔ `malaria_df$cases` accesses the **'cases'** column of the data frame  

---

### **Step 4: Subsetting Data with Conditions**
```r
# Subsetting the data to find cases greater than 200
subset_df <- malaria_df[malaria_df$cases > 200, ]
```
### **🔍 Explanation:**  
✔ `malaria_df[malaria_df$cases > 200, ]` subsets rows where **cases are greater than 200**  

---

## **3️⃣ Basic Functions for Malaria Data Analysis**

### **Step 1: `mean()`**
```r
# Calculating the mean number of cases
mean_cases <- mean(malaria_df$cases)
```
### **🔍 Explanation:**  
✔ `mean()` calculates the **average** of the `cases` column  
✔ `mean_cases` stores the result of the average malaria cases  

---

### **Step 2: `sum()`**
```r
# Calculating the total number of malaria cases
total_cases <- sum(malaria_df$cases)
```
### **🔍 Explanation:**  
✔ `sum()` calculates the **sum** of the `cases` column  
✔ `total_cases` stores the result of the total malaria cases  

---

### **Step 3: `table()`**
```r
# Counting the occurrences of each unique value in the region column
region_counts <- table(malaria_df$region)
```
### **🔍 Explanation:**  
✔ `table()` counts the **frequency** of each value in the specified column (e.g., `region`)  
✔ `region_counts` stores the count of malaria cases per region  

---

### **Step 4: `summary()`**
```r
# Generating summary statistics of the data frame
summary_stats <- summary(malaria_df)
```
### **🔍 Explanation:**  
✔ `summary()` generates **summary statistics** for each column (min, max, mean, etc.) in the data frame  
✔ `summary_stats` stores the resulting statistics  

---

## **4️⃣ Data Cleaning with `dplyr`**

### **Step 1: Installing and Loading `dplyr`**
```r
# Install dplyr package
install.packages("dplyr")

# Load the dplyr package
library(dplyr)
```
### **🔍 Explanation:**  
✔ `install.packages("dplyr")` installs the `dplyr` package, which simplifies data manipulation  
✔ `library(dplyr)` loads the package into the R environment  

---

### **Step 2: `filter()` – Filtering Rows**
```r
# Filter rows where cases are greater than 200
filtered_df <- filter(malaria_df, cases > 200)
```
### **🔍 Explanation:**  
✔ `filter()` selects **rows** that meet the condition (cases > 200)  
✔ `filtered_df` stores the filtered dataset  

---

### **Step 3: `select()` – Selecting Columns**
```r
# Select only the 'region' and 'cases' columns
selected_df <- select(malaria_df, region, cases)
```
### **🔍 Explanation:**  
✔ `select()` picks specific **columns** from the data frame  
✔ `selected_df` contains only the `region` and `cases` columns  

---

### **Step 4: `mutate()` – Adding/Modifying Columns**
```r
# Create a new column 'cases_per_1000' by dividing cases by 1000
malaria_df <- mutate(malaria_df, cases_per_1000 = cases / 1000)
```
### **🔍 Explanation:**  
✔ `mutate()` creates or modifies a **column** in the data frame  
✔ `cases_per_1000` is a new column showing cases per 1000 people  

---

## **✅ Summary of Week 2**  
By the end of this week, you should:  
✔ **Understand basic R data structures**: vectors, matrices, lists, and data frames  
✔ **Know how to index and subset data**  
✔ **Be able to apply basic functions**: `mean()`, `sum()`, `table()`, `summary()`  
✔ **Have learned to clean data with `dplyr`**: `filter()`, `select()`, `mutate()`

--- 


# **📌 Week 2: Exercises – Data Cleaning and Visualization with R for Malaria Data Analysis**  

This week’s exercises will focus on **data cleaning, outlier detection, and data visualization**. The goal is to prepare the malaria dataset for analysis by handling missing values, outliers, and creating visualizations. Follow along step by step!

---

## **1️⃣ Data Cleaning and Preprocessing**  

### **Exercise 1.1: Handle Missing Values**  
🔹 **You have a dataset called `malaria_data` with the following columns:**  
- `Region`  
- `Cases`  
- `Fatalities`  
- `Recovered`

Some values in the `Cases` column are missing.  

**Write the R code to:**  
1. Find the number of missing values in the `Cases` column.  
2. Replace the missing values with the **mean** of the `Cases` column.

---

### **Exercise 1.2: Remove Rows with Missing Data**  
🔹 **Using the `na.omit()` function, remove rows with any missing values from the `malaria_data` dataframe.**  

**Write the R code to:**  
1. Use `na.omit()` to remove rows with missing data.  
2. Display the cleaned dataframe.

---

### **Exercise 1.3: Handle Outliers**  
🔹 **Detect and remove outliers in the `Cases` column using the Interquartile Range (IQR).**  
- The formula for detecting outliers is:  
  ```math
  Lower bound = Q1 - 1.5 * IQR
  Upper bound = Q3 + 1.5 * IQR
  ```
  Where **Q1** is the first quartile and **Q3** is the third quartile.  

**Write the R code to:**  
1. Calculate Q1, Q3, and IQR for the `Cases` column.  
2. Remove outliers from the `Cases` column.  
3. Display the cleaned dataset.

---

## **2️⃣ Data Manipulation with dplyr**  

### **Exercise 2.1: Filter Data by Condition**  
🔹 **Use the `filter()` function from `dplyr` to filter out malaria cases where the number of `Cases` is less than 500.**  

**Write the R code to:**  
1. Filter `malaria_data` to keep rows where `Cases > 500`.  
2. Display the filtered dataset.

---

### **Exercise 2.2: Arrange Data**  
🔹 **Use the `arrange()` function from `dplyr` to sort the data in descending order based on the `Cases` column.**  

**Write the R code to:**  
1. Sort the `malaria_data` dataframe by `Cases` in descending order.  
2. Display the sorted dataset.

---

### **Exercise 2.3: Create a New Column**  
🔹 **Create a new column called `FatalityRate` that calculates the fatality rate as:**  
```math
FatalityRate = Fatalities / Cases * 100
```

**Write the R code to:**  
1. Add a new column `FatalityRate` to the `malaria_data` dataframe.  
2. Display the updated dataframe.

---

## **3️⃣ Data Visualization with ggplot2**  

### **Exercise 3.1: Create a Histogram**  
🔹 **Use the `ggplot2` package to create a histogram of the `Cases` column from `malaria_data`.**  

**Write the R code to:**  
1. Create a histogram of the `Cases` column.  
2. Customize the plot with a title and axis labels.

---

### **Exercise 3.2: Create a Scatter Plot**  
🔹 **Use the `ggplot2` package to create a scatter plot showing the relationship between `Cases` and `Fatalities`.**  

**Write the R code to:**  
1. Create a scatter plot with `Cases` on the x-axis and `Fatalities` on the y-axis.  
2. Add a title and axis labels to the plot.

---

### **Exercise 3.3: Create a Boxplot**  
🔹 **Use the `ggplot2` package to create a boxplot to visualize the distribution of `Cases`.**  

**Write the R code to:**  
1. Create a boxplot of the `Cases` column.  
2. Add a title to the plot and customize the colors.

---

## **4️⃣ Bonus Challenge: Automate Data Cleaning and Visualization**  

🔹 **Write an R script that:**  
1. **Asks the user** for a file path of a CSV file containing malaria data.  
2. **Loads the dataset** into R.  
3. **Cleans the data** by handling missing values and outliers (use previous steps).  
4. **Creates visualizations**:  
   - A histogram of `Cases`  
   - A scatter plot of `Cases` vs `Fatalities`  
5. **Saves the cleaned dataset** to a new CSV file.

📌 **Hint:** Use `read_csv()`, `summary()`, `write_csv()`, and the visualization functions you learned earlier.

---


Here are the **solutions** for **Week 2: Data Cleaning and Visualization with R for Malaria Data Analysis**:

---

## **1️⃣ Data Cleaning and Preprocessing**

### **Exercise 1.1: Handle Missing Values**  
```r
# Find the number of missing values in the 'Cases' column
missing_values <- sum(is.na(malaria_data$Cases))
missing_values

# Replace missing values with the mean of the 'Cases' column
mean_cases <- mean(malaria_data$Cases, na.rm = TRUE)
malaria_data$Cases[is.na(malaria_data$Cases)] <- mean_cases
```

**Explanation:**
- `is.na()` checks for missing values in the `Cases` column.
- `mean()` calculates the mean of the `Cases` column, excluding missing values with `na.rm = TRUE`.
- Missing values are replaced with the computed mean.

---

### **Exercise 1.2: Remove Rows with Missing Data**  
```r
# Remove rows with any missing values using na.omit()
malaria_data_cleaned <- na.omit(malaria_data)

# Display the cleaned dataframe
head(malaria_data_cleaned)
```

**Explanation:**
- `na.omit()` removes rows with any missing values in the entire dataframe.

---

### **Exercise 1.3: Handle Outliers**  
```r
# Calculate Q1, Q3, and IQR for the 'Cases' column
Q1 <- quantile(malaria_data$Cases, 0.25, na.rm = TRUE)
Q3 <- quantile(malaria_data$Cases, 0.75, na.rm = TRUE)
IQR <- Q3 - Q1

# Calculate the lower and upper bounds for outlier detection
lower_bound <- Q1 - 1.5 * IQR
upper_bound <- Q3 + 1.5 * IQR

# Remove outliers from the 'Cases' column
malaria_data_no_outliers <- malaria_data[malaria_data$Cases >= lower_bound & malaria_data$Cases <= upper_bound, ]

# Display the cleaned dataset
head(malaria_data_no_outliers)
```

**Explanation:**
- `quantile()` computes the first (Q1) and third (Q3) quartiles.
- IQR is calculated as the difference between Q3 and Q1.
- Outliers are removed based on the lower and upper bounds, defined by 1.5 times the IQR.

---

## **2️⃣ Data Manipulation with dplyr**

### **Exercise 2.1: Filter Data by Condition**  
```r
# Filter the data to keep rows where 'Cases' > 500
library(dplyr)
malaria_data_filtered <- filter(malaria_data, Cases > 500)

# Display the filtered dataset
head(malaria_data_filtered)
```

**Explanation:**
- `filter()` from `dplyr` is used to keep only the rows where `Cases > 500`.

---

### **Exercise 2.2: Arrange Data**  
```r
# Sort the data in descending order based on the 'Cases' column
malaria_data_sorted <- arrange(malaria_data, desc(Cases))

# Display the sorted dataset
head(malaria_data_sorted)
```

**Explanation:**
- `arrange()` from `dplyr` is used to sort the data. The `desc()` function is used to sort in descending order.

---

### **Exercise 2.3: Create a New Column**  
```r
# Create a new column 'FatalityRate' in the dataframe
malaria_data$FatalityRate <- (malaria_data$Fatalities / malaria_data$Cases) * 100

# Display the updated dataframe
head(malaria_data)
```

**Explanation:**
- The `FatalityRate` is calculated by dividing `Fatalities` by `Cases` and multiplying by 100.

---

## **3️⃣ Data Visualization with ggplot2**

### **Exercise 3.1: Create a Histogram**  
```r
# Load ggplot2 for visualization
library(ggplot2)

# Create a histogram of the 'Cases' column
ggplot(malaria_data, aes(x = Cases)) +
  geom_histogram(binwidth = 100, fill = "blue", color = "black") +
  labs(title = "Distribution of Malaria Cases", x = "Cases", y = "Frequency")
```

**Explanation:**
- `geom_histogram()` creates the histogram with custom bin width.
- `labs()` adds a title and labels to the axes.

---

### **Exercise 3.2: Create a Scatter Plot**  
```r
# Create a scatter plot of 'Cases' vs 'Fatalities'
ggplot(malaria_data, aes(x = Cases, y = Fatalities)) +
  geom_point(color = "red") +
  labs(title = "Malaria Cases vs Fatalities", x = "Cases", y = "Fatalities")
```

**Explanation:**
- `geom_point()` creates a scatter plot. The points are colored red for visual distinction.
- `labs()` adds the title and axis labels.

---

### **Exercise 3.3: Create a Boxplot**  
```r
# Create a boxplot of the 'Cases' column
ggplot(malaria_data, aes(y = Cases)) +
  geom_boxplot(fill = "lightgreen", color = "black") +
  labs(title = "Boxplot of Malaria Cases", y = "Cases")
```

**Explanation:**
- `geom_boxplot()` creates the boxplot. The box is filled with light green and outlined in black.
- `labs()` adds a title and y-axis label.

---

## **4️⃣ Bonus Challenge: Automate Data Cleaning and Visualization**

```r
# Ask the user for the file path
file_path <- readline(prompt = "Enter the path to the CSV file: ")

# Load the dataset
library(readr)
malaria_data <- read_csv(file_path)

# Clean the data by handling missing values and outliers
malaria_data$Cases[is.na(malaria_data$Cases)] <- mean(malaria_data$Cases, na.rm = TRUE)

# Calculate Q1, Q3, and IQR for 'Cases' column
Q1 <- quantile(malaria_data$Cases, 0.25, na.rm = TRUE)
Q3 <- quantile(malaria_data$Cases, 0.75, na.rm = TRUE)
IQR <- Q3 - Q1
lower_bound <- Q1 - 1.5 * IQR
upper_bound <- Q3 + 1.5 * IQR
malaria_data <- malaria_data[malaria_data$Cases >= lower_bound & malaria_data$Cases <= upper_bound, ]

# Create visualizations
library(ggplot2)
ggplot(malaria_data, aes(x = Cases)) +
  geom_histogram(binwidth = 100, fill = "blue", color = "black") +
  labs(title = "Distribution of Malaria Cases", x = "Cases", y = "Frequency")

ggplot(malaria_data, aes(x = Cases, y = Fatalities)) +
  geom_point(color = "red") +
  labs(title = "Malaria Cases vs Fatalities", x = "Cases", y = "Fatalities")

# Save the cleaned dataset to a new CSV file
write_csv(malaria_data, "cleaned_malaria_data.csv")
```

**Explanation:**
- The script asks the user for a file path and loads the dataset using `read_csv()`.
- It handles missing values and outliers (as described in previous steps).
- It creates the histogram and scatter plot for visualizations.
- Finally, it saves the cleaned dataset using `write_csv()`.

---

## **💡 Additional Notes:**
- Make sure to have the required libraries (`ggplot2`, `dplyr`, `readr`, etc.) installed before running the code.
- For the bonus challenge, ensure the path to the CSV file is correct, and if running on an interactive system like RStudio, input the file path properly.

---


## **💡 What’s Next?**  
✔ After completing these exercises, you will have learned how to clean and visualize malaria data.  
✔ In **Week 3**, we will dive deeper into advanced analysis techniques such as grouping, summarizing, and advanced plotting! 🚀

