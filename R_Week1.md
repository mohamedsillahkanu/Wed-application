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
