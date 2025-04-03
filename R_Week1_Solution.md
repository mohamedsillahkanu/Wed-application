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

