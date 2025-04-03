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
