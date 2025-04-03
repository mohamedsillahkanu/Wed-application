# **📅 Week 1: Introduction to R & RStudio for Malaria Data Analysis**  

This week, we will:  
✅ **Set up R and RStudio**  
✅ **Learn basic R syntax**  
✅ **Use R Markdown for documentation**  
✅ **Read malaria datasets (CSV, Excel) into R step by step**  

---

## **1️⃣ Installing R and RStudio**  

### **Why Use R and RStudio?**  
✔ **R** is a powerful language for **data analysis, statistics, and visualization**.  
✔ **RStudio** makes working with R easier by providing a user-friendly interface.  

### **Step 1: Install R**  
1. Go to [CRAN](https://cran.r-project.org/)  
2. Download and install R for your operating system  

### **Step 2: Install RStudio**  
1. Go to [Posit](https://posit.co/download/rstudio-desktop/)  
2. Download **RStudio Desktop** and install it  

### **Step 3: Open RStudio**  
When you open RStudio, you'll see:  
📌 **Console** – Run R commands interactively  
📌 **Script Editor** – Write and save R scripts (`.R` files)  
📌 **Environment Pane** – View variables and datasets  
📌 **Plots Pane** – Display graphs and tables  

---

## **2️⃣ Basic R Syntax**  

### **Step 1: Assigning Variables**
```r
cases <- 150          # Number of malaria cases
fatality_rate <- 4.2  # Fatality rate in percentage
region <- "West"      # Region name (text)
outbreak <- TRUE      # Logical value (Boolean)
```
### **🔍 Explanation:**  
✔ `cases <- 150` assigns `150` to `cases`  
✔ `fatality_rate <- 4.2` stores `4.2` in `fatality_rate`  
✔ `region <- "West"` stores `"West"` as a text string  
✔ `outbreak <- TRUE` stores a **Boolean** value (TRUE/FALSE)  

---

### **Step 2: Checking Data Types**
```r
class(cases)          # Output: "numeric"
class(region)         # Output: "character"
class(outbreak)       # Output: "logical"
```
### **🔍 Explanation:**  
✔ `class()` function shows the data type of each variable  
✔ `"numeric"` means numbers  
✔ `"character"` means text  
✔ `"logical"` means **TRUE or FALSE**  

---

### **Step 3: Basic Operators**
```r
total_cases <- cases + 50   # Adding 50 more cases
fatalities <- cases * (fatality_rate / 100)  # Calculating fatalities
recovered <- cases - fatalities  # Subtracting fatalities from total cases
```
### **🔍 Explanation:**  
✔ `cases + 50` adds 50 cases  
✔ `cases * (fatality_rate / 100)` converts percentage to decimal and calculates fatalities  
✔ `cases - fatalities` finds the number of recovered patients  

---

## **3️⃣ R Markdown for Documentation**  

### **What is R Markdown?**  
📌 **R Markdown** lets you create **reports, notebooks, and presentations** with **text, R code, and results** in one document.  

### **Step 1: Install R Markdown**
```r
install.packages("rmarkdown")  # Installs R Markdown package
```
### **🔍 Explanation:**  
✔ `install.packages("rmarkdown")` installs the package to generate documents in **HTML, PDF, or Word**  

---

### **Step 2: Create an R Markdown File**  
1. Open **RStudio**  
2. Click **File → New File → R Markdown**  
3. Select **HTML, PDF, or Word output format**  
4. Click **OK**  

---

### **Step 3: Writing R Markdown Code**
````r
# Malaria Data Analysis  

This document presents an analysis of malaria cases.

```{r}
summary(cases)  # Shows summary statistics of 'cases'
```
````  
### **🔍 Explanation:**  
✔ `#` starts a **comment**  
✔ `summary(cases)` calculates **min, max, mean, and median** of `cases`  
✔ Text outside `{r}` is normal text in the report  

📌 Click **Knit** in RStudio to generate an **HTML, PDF, or Word** document.  

---

## **4️⃣ Reading Malaria Datasets (CSV, Excel) in R**  

### **Why Read External Data?**  
📌 Malaria data is stored in **CSV (Comma-Separated Values) or Excel** files.  
📌 We use **`readr`** and **`readxl`** to load these files into R.  

---

### **Step 1: Install Required Packages**  
```r
install.packages("readr")   # Install readr package for CSV files
install.packages("readxl")  # Install readxl package for Excel files
```
### **🔍 Explanation:**  
✔ `install.packages("readr")` installs `readr` (for CSV files)  
✔ `install.packages("readxl")` installs `readxl` (for Excel files)  

---

### **📂 4.1 Reading CSV Files with `readr`**  
```r
library(readr)  # Load readr package

# Read malaria data from a CSV file
malaria_data <- read_csv("malaria_cases.csv")

# View first few rows
head(malaria_data)
```
### **🔍 Explanation:**  
✔ `library(readr)` loads the **`readr`** package  
✔ `read_csv("malaria_cases.csv")` reads the CSV file into a **dataframe**  
✔ `malaria_data` stores the **imported dataset**  
✔ `head(malaria_data)` shows the **first 6 rows** of the dataset  

---

### **📂 4.2 Reading Excel Files with `readxl`**  
```r
library(readxl)  # Load readxl package

# Read malaria data from an Excel file
malaria_data_excel <- read_excel("malaria_cases.xlsx", sheet = 1)

# View first few rows
head(malaria_data_excel)
```
### **🔍 Explanation:**  
✔ `library(readxl)` loads the **`readxl`** package  
✔ `read_excel("malaria_cases.xlsx", sheet = 1)` reads **Sheet 1** of the Excel file  
✔ `malaria_data_excel` stores the **imported dataset**  
✔ `head(malaria_data_excel)` shows the **first 6 rows**  

---

### **📌 4.3 Writing Data to CSV and Excel**  

#### **Saving as CSV**
```r
write_csv(malaria_data, "cleaned_malaria_data.csv")
```
### **🔍 Explanation:**  
✔ `write_csv(malaria_data, "cleaned_malaria_data.csv")` saves **`malaria_data`** as a CSV file  

---

#### **Saving as Excel**
```r
install.packages("writexl")  # Install writexl package
library(writexl)  # Load writexl

write_xlsx(malaria_data, "cleaned_malaria_data.xlsx")
```
### **🔍 Explanation:**  
✔ `install.packages("writexl")` installs **`writexl`** for writing Excel files  
✔ `library(writexl)` loads the **`writexl`** package  
✔ `write_xlsx(malaria_data, "cleaned_malaria_data.xlsx")` saves data as an **Excel file**  

---

## **✅ Summary of Week 1**  
By the end of this week, you should:  
✔ **Install R and RStudio**  
✔ **Understand basic R syntax** (variables, operators)  
✔ **Use R Markdown for documentation**  
✔ **Read and write malaria datasets (CSV, Excel)**  

---

# **📌 Week 1: Exercises – Introduction to R & RStudio for Malaria Data Analysis**  

These exercises will help you practice **basic R syntax, data types, and reading/writing malaria datasets.** Try them step by step.  

---

## **1️⃣ Basic R Syntax and Operations**  
Create variables related to malaria cases and perform simple calculations.  

### **Exercise 1.1: Assign Values**  
🔹 **Create the following variables in R:**  
- `total_cases` = **500** (Total malaria cases)  
- `fatality_rate` = **3.5** (Fatality rate in percentage)  
- `region` = **"North"** (Name of the region)  
- `outbreak` = **TRUE** (Logical value indicating outbreak status)  

✍ **Write the R code to assign these values.**  

---

### **Exercise 1.2: Check Data Types**  
🔹 **Use `class()` to check the data type of each variable created above.**  

**Example Output:**  
```
[1] "numeric"
[1] "character"
[1] "logical"
```
✍ **Write the R code to check the types.**  

---

### **Exercise 1.3: Perform Calculations**  
Using the variables created earlier, calculate:  
1. **Estimated fatalities**:  
   ```math
   fatalities = total_cases × (fatality_rate / 100)
   ```  
2. **Recovered cases**:  
   ```math
   recovered = total_cases - fatalities
   ```  
✍ **Write the R code to calculate these values.**  

---

## **2️⃣ Using R Markdown**  

### **Exercise 2.1: Install and Load R Markdown**  
🔹 **Write the R command to install and load the `rmarkdown` package.**  

---

### **Exercise 2.2: Create an R Markdown File**  
1. **In RStudio**, go to **File → New File → R Markdown**  
2. **Choose** an output format (**HTML, PDF, or Word**)  
3. **Write a short summary** about malaria cases in your document  
4. **Include an R code chunk** that displays the summary of `total_cases`  

✍ **Follow the steps and create your first R Markdown document!**  

---

## **3️⃣ Reading and Writing Data (CSV, Excel)**  

### **Exercise 3.1: Install and Load Data Packages**  
🔹 **Write the R commands to install and load `readr` and `readxl`.**  

---

### **Exercise 3.2: Read a CSV File**  
Suppose you have a malaria dataset **`malaria_data.csv`** with the following columns:  

| Region  | Cases | Fatalities | Recovered |
|---------|-------|------------|------------|
| North   | 500   | 20         | 480        |
| South   | 300   | 10         | 290        |
| East    | 700   | 35         | 665        |

**Write the R code to:**  
1. Load the **`readr`** package  
2. Read the **CSV file** into a dataframe called `malaria_df`  
3. Display the **first 6 rows** of the dataframe  

---

### **Exercise 3.3: Read an Excel File**  
If the same data is in **`malaria_data.xlsx` (Sheet 1)**, **write the R code** to:  
1. Load the **`readxl`** package  
2. Read the **Excel file** into a dataframe called `malaria_excel_df`  
3. Display the **first 6 rows**  

---

### **Exercise 3.4: Write Data to CSV and Excel**  
After analyzing the malaria dataset, save it as:  
1. **CSV file**: `"processed_malaria_data.csv"`  
2. **Excel file**: `"processed_malaria_data.xlsx"`  

**Write the R code to do this!**  

---

## **4️⃣ Bonus Challenge: Automate CSV Import**  
🔹 **Write an R script that:**  
1. **Asks the user** for a CSV file path  
2. **Loads the dataset**  
3. **Displays summary statistics**  
4. **Saves the cleaned dataset as a new CSV file**  

📌 **Hint:** Use `read_csv()`, `summary()`, and `write_csv()`.  

---

## **💡 What’s Next?**  
✔ Try these exercises in RStudio  
✔ If you have questions, ask for hints!  
✔ Get ready for **Week 2: Data Cleaning & Visualization!** 🚀  


---

# **📌 Week 1: Solution scripts – Introduction to R & RStudio for Malaria Data Analysis**  
Here are the **solutions** for the Week 1 exercises:
---

## **1️⃣ Basic R Syntax and Operations**

### **Exercise 1.1: Assign Values**  
```r
# Assigning values to variables
total_cases <- 500
fatality_rate <- 3.5
region <- "North"
outbreak <- TRUE
```

---

### **Exercise 1.2: Check Data Types**  
```r
# Check the data types of the variables
class(total_cases)     # numeric
class(fatality_rate)   # numeric
class(region)          # character
class(outbreak)        # logical
```

**Explanation:**
- `class()` returns the data type of the variable.

---

### **Exercise 1.3: Perform Calculations**  
```r
# Calculating fatalities and recovered cases
fatalities <- total_cases * (fatality_rate / 100)
recovered <- total_cases - fatalities

# Displaying the results
fatalities
recovered
```

**Explanation:**
- The formula for fatalities is `total_cases * (fatality_rate / 100)`.
- The formula for recovered cases is `total_cases - fatalities`.

---

## **2️⃣ Using R Markdown**

### **Exercise 2.1: Install and Load R Markdown**  
```r
# Installing and loading the rmarkdown package
install.packages("rmarkdown")
library(rmarkdown)
```

---

### **Exercise 2.2: Create an R Markdown File**

1. Open RStudio and go to **File → New File → R Markdown**.
2. Choose the output format (HTML, PDF, Word).
3. Write the following example R Markdown document content:

```markdown
---
title: "Malaria Data Summary"
output: html_document
---

## Malaria Cases Summary

The total malaria cases in the region are `r total_cases`.  
The fatality rate is `r fatality_rate`.  
The total fatalities are calculated as `r fatalities`.

``` 

4. Click **Knit** to generate the HTML output.

---

## **3️⃣ Reading and Writing Data (CSV, Excel)**

### **Exercise 3.1: Install and Load Data Packages**  
```r
# Installing and loading the necessary packages
install.packages("readr")
install.packages("readxl")

library(readr)
library(readxl)
```

---

### **Exercise 3.2: Read a CSV File**  
```r
# Reading the CSV file into a dataframe
malaria_df <- read_csv("malaria_data.csv")

# Displaying the first 6 rows of the dataframe
head(malaria_df)
```

**Explanation:**
- `read_csv()` reads CSV files into a dataframe.
- `head()` displays the first 6 rows of the dataframe.

---

### **Exercise 3.3: Read an Excel File**  
```r
# Reading the Excel file into a dataframe
malaria_excel_df <- read_excel("malaria_data.xlsx", sheet = 1)

# Displaying the first 6 rows of the dataframe
head(malaria_excel_df)
```

**Explanation:**
- `read_excel()` reads Excel files into a dataframe.
- `sheet = 1` specifies the sheet to read (sheet 1).

---

### **Exercise 3.4: Write Data to CSV and Excel**  
```r
# Writing data to a CSV file
write_csv(malaria_df, "processed_malaria_data.csv")

# Writing data to an Excel file
write.xlsx(malaria_df, "processed_malaria_data.xlsx")
```

**Explanation:**
- `write_csv()` saves the dataframe as a CSV file.
- `write.xlsx()` saves the dataframe as an Excel file.

---

## **4️⃣ Bonus Challenge: Automate CSV Import**

```r
# Asking the user for the file path
file_path <- readline(prompt = "Enter the path to the CSV file: ")

# Reading the dataset from the provided path
malaria_data <- read_csv(file_path)

# Displaying summary statistics
summary(malaria_data)

# Saving the cleaned data to a new CSV file
write_csv(malaria_data, "cleaned_malaria_data.csv")
```

**Explanation:**
- `readline()` is used to ask the user for input (file path).
- `summary()` gives the summary statistics of the dataset.
- `write_csv()` saves the dataframe as a CSV file.

---

## **💡 Additional Notes:**  
- Make sure that the paths to the files are correct, and if you're reading from an Excel file, ensure that the `readxl` library is loaded.
- If you get errors when trying to install packages, make sure you have an active internet connection, and the R version is up-to-date.
---




