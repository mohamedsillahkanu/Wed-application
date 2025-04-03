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

## **💡 What’s Next?**  
✔ After completing these exercises, you will have learned how to clean and visualize malaria data.  
✔ In **Week 3**, we will dive deeper into advanced analysis techniques such as grouping, summarizing, and advanced plotting! 🚀
