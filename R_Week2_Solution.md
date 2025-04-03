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
