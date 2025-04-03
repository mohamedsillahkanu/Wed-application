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
