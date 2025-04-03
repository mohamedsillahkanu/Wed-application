### 📌 **Week 2: Data Structures & Basic Operations**  

In **Week 2**, we will explore the core **data structures** in R and focus on basic operations such as **indexing, subsetting**, and using **basic functions** to analyze malaria data. We will also cover **data cleaning** using `dplyr` for filtering, selecting, and mutating data.

---

### **💡 Key Concepts Covered**  
1. **Data Structures**: Learn about vectors, matrices, lists, and data frames.  
2. **Indexing & Subsetting**: Understand how to extract subsets of data based on specific conditions.  
3. **Basic Functions**: Learn functions like `mean()`, `sum()`, `table()`, and `summary()` to summarize and perform operations on the data.  
4. **Data Cleaning with dplyr**: Introduction to the `dplyr` package for **filtering**, **selecting**, and **mutating** data.

---

## **1️⃣ Data Structures: Vectors, Matrices, Lists, and Data Frames**

### **1.1 Vectors**
- A **vector** is a one-dimensional collection of elements of the same type (numeric, character, etc.).
- You create a vector using `c()`.

#### **Example**:

```r
# Create a vector of malaria cases by region
malaria_cases <- c(500, 300, 700, 450, 600)
```

- **Access elements** using indexing:
  
```r
malaria_cases[1]  # Access the first element: 500
```

### **1.2 Matrices**
- A **matrix** is a two-dimensional collection of elements of the same type (numeric, character, etc.).
- Create a matrix using `matrix()`.
  
#### **Example**:

```r
# Create a matrix representing malaria cases in different regions and months
malaria_matrix <- matrix(c(500, 300, 700, 450, 600, 200, 550, 400), 
                        nrow = 4, ncol = 2, 
                        dimnames = list(c("North", "South", "East", "West"),
                                        c("January", "February")))
```

- **Access elements** in a matrix using row and column indices:
  
```r
malaria_matrix[2, 2]  # Access value in the second row and second column (South, February)
```

### **1.3 Lists**
- A **list** can contain different types of data structures such as vectors, matrices, and data frames.
  
#### **Example**:

```r
# Create a list containing different data types
malaria_list <- list(
  cases = malaria_cases,
  stats = malaria_matrix,
  region = "West Africa"
)
```

- **Access list elements**:

```r
malaria_list$cases  # Access the vector of malaria cases
```

### **1.4 Data Frames**
- A **data frame** is a table-like structure, where columns can contain different data types.
- Create a data frame using `data.frame()`.

#### **Example**:

```r
# Create a data frame of malaria cases and fatalities by region
malaria_df <- data.frame(
  Region = c("North", "South", "East", "West"),
  Cases = c(500, 300, 700, 450),
  Fatalities = c(20, 10, 35, 15)
)
```

- **Access columns** and rows using `$` or indexing:

```r
malaria_df$Cases  # Access the 'Cases' column
malaria_df[1, ]   # Access the first row
```

---

## **2️⃣ Indexing & Subsetting Malaria Data**

### **2.1 Indexing Vectors**

- **Indexing** allows you to access specific elements within a vector or data frame.

#### **Example**:

```r
# Subset the malaria cases vector
malaria_cases[1:3]  # Extract the first three malaria cases
```

### **2.2 Subsetting Data Frames**

- Use logical conditions to subset rows of a data frame based on specific criteria.

#### **Example**:

```r
# Subset data frame to include only rows where Cases are greater than 400
subset_malaria <- malaria_df[malaria_df$Cases > 400, ]
```

### **2.3 Selecting Specific Columns**

- Use `select()` to choose specific columns from a data frame, especially when working with large datasets.

#### **Example**:

```r
# Select only the 'Region' and 'Cases' columns
selected_data <- select(malaria_df, Region, Cases)
```

---

## **3️⃣ Basic Functions**

### **3.1 mean() & sum()**

- **`mean()`** computes the average of a numeric vector.
- **`sum()`** calculates the total sum of a numeric vector.

#### **Example**:

```r
# Calculate the mean of malaria cases
mean(malaria_cases)  # Output: 510

# Calculate the total number of malaria cases
sum(malaria_cases)  # Output: 2550
```

### **3.2 summary()**

- **`summary()`** provides a quick summary of a data frame, including the minimum, maximum, mean, median, and other statistics for each column.

#### **Example**:

```r
# Get summary statistics for the malaria data frame
summary(malaria_df)
```

### **3.3 table()**

- **`table()`** counts the frequency of each unique value in a vector.

#### **Example**:

```r
# Count the frequency of malaria cases across regions
table(malaria_df$Region)
```

---

## **4️⃣ Data Cleaning with `dplyr`**

The `dplyr` package in R is a powerful tool for **data manipulation**. We'll focus on three key functions:

- **filter()**: Subsets data based on conditions.
- **select()**: Selects specific columns from the data.
- **mutate()**: Adds or modifies columns in the data.

### **4.1 filter()**

- **`filter()`** is used to filter rows based on conditions.

#### **Example**:

```r
# Filter rows where the number of cases is greater than 400
filtered_data <- filter(malaria_df, Cases > 400)
```

### **4.2 select()**

- **`select()`** helps you choose specific columns from a data frame.

#### **Example**:

```r
# Select columns 'Region' and 'Fatalities' from the data
selected_columns <- select(malaria_df, Region, Fatalities)
```

### **4.3 mutate()**

- **`mutate()`** allows you to create or modify columns in a data frame.

#### **Example**:

```r
# Create a new column 'Case_Fatality_Rate' by dividing Fatalities by Cases
malaria_df <- mutate(malaria_df, Case_Fatality_Rate = Fatalities / Cases)
```

---

## **Summary**

This week, we have covered the basics of data structures in R, learned how to index and subset data, and practiced using functions like `mean()`, `sum()`, and `summary()` to perform simple analyses. We also explored data cleaning with `dplyr` using `filter()`, `select()`, and `mutate()` to manipulate malaria data.
