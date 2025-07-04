# R Programming for Data Science: Introduction  

## Formative Assignment (Non-graded)

**Due Date:** 4 June 2025, 10:59 PM GMT  
**Release Date:** 18 May 2025, 11:00 PM GMT 

**Submission Format:** Word Document or PDF  
**Submission Method:** Email to `weeklyclasses@conted.ox.ac.uk`  
**Attach:** Completed Declaration of Authorship form

---

## Overview

This formative assignment is designed to help you consolidate key concepts in R programming, including vectorization, control flow, function writing, data manipulation, and basic visualization. You are encouraged to reference course materials and seek additional learning resources if needed.

---

## Assignment Questions

### Q1: R Programming Concepts

Answer each question in **no more than 60 words**:

- **a)** What is vectorization in R, and what are its benefits?

```
  - Vectorisation is an implicit process in R where an operation can be performed on each element of a vector.
  - A benefit of vectorisation is that the code becomes more readable because there is no need to explicitly loop over elements of a vector.
  - For example, two vectors can be added together, or   a numerical value can be multiplied for all the vector values. (Matloff, 2011)
```  

- **b)** What is recycling in R? Provide an example.

```  
  - Recycling rules apply when performing operations on vectors of different lengths.
  - If one variable is a single number, it is treated as a vector matching the length of the other variable.
  - R will recycle the shorter vector if the longer vector's length is a multiple of the shorter vector's length.
  - Otherwise, it issues a warning and performs the operation on overlapping elements.(Hadley, 2025)
```

- **c)** What is operator precedence? Provide an R example.

```
  - Operator precedence in computer science simply means the order which mathematical and 
    logical operations are to be performed
  - One notable exception any operation in side brackets are performed first from left to 
    right
  - Examples in R
```

This example 3 * 3 is performed before any additions according to order of precedence

``` r
    a <- 3 * 3 + 2
    cat("a: ", a)
    a:  11 # result of print out
```


This example 3 + 2 is performed due to ( ) has higher precedence than
multiplication


``` r
    b <- 3 * (3 + 2)
    cat ("b: ", b)
    b:  15 # result of print out 
```
- **d)** What is function scope, and why is it important?

```  
  - Scope denotes the visibility or accessibility of variables and functions.
  - Variables defined in the global or higher scope will be visible within any function    
    defined within the script.
  - Variables or functions defined within a function will only be visible within that 
    function's scope.
  - In the event of naming conflict, the definition and assignment within the     
    function's scope takes precedence over higher scopes, including global scope.
  - Understanding the function scope is essential for tracking names,
    assignments, and values of variables and functions at any moment.
```

---

### Q2: Control Flow and Looping

- **a)** Write an R function `fibonacci(n)` that returns the first `n` Fibonacci numbers as a vector.

``` r
Return vector of numbers 
#' Example fibonacci_function(5)
#' # Output: "0, 1, 1, 2, 3"
fibonacci_function <- function(term_number) {
  # starting values
  first_term = 0
  second_term = 1
  # substracting 1 from the number term because we are starting from 0
  term_number = term_number - 1
  # starting value is set to 0 for starting term
  current_term = 0
  # adding first two elements to list
  fibo_values <- list(first_term, second_term)
  # only valid for when term number is great than 2
  if (term_number > 2) {
    for (x in 2:term_number) {
      current_term = first_term + second_term
      fibo_values <- append(fibo_values, current_term)
      first_term = second_term
      second_term = current_term
    }
    
  # if term is 1 then simply return the term number which can be either 1, 0, negative
  } else {
    fibo_values <- (term_number)
  }
  # print Fibonacci array
  result <- toString(fibo_values)
  return(result)
}
```

- **b)** Write a `while` loop that prints Fibonacci numbers **until their sum exceeds 1000**.

``` r
#' input parameters: term_number Integer. The number of terms in the Fibonacci sequence to compute.
#'
#' return:  No return value. Prints the Fibonacci sequence.
#'
#' details:
#' - The Fibonacci sequence starts with 0 and 1.
#' - If `term_number` <= 2, the function handles the case differently and simply returns the index.
#' - If `term_number` is greater than 2, the function constructs a sequence iteratively.
#' - if `sum of fibonacci values ` is greater than sub_limit it will then terminate
#'
#' examples
#' fibonacci_function(16,1000)
#' Accumulated Value:  1596 Exceeds:  1000
#' Fibonacci Sequence:  0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610
fibonacci_function <- function(sum_limit) {
  # starting values
  first_term = 0
  second_term = 1
  # starting value is set to 0 for starting term
  current_term = 0
  # adding first two elements to list
  # only valid for when term number is great than 2
  # set accumulated to starting value, 0
  accumulated_sum = 0
  # Keeping running 
  while (TRUE) {
    # Current term becomes first term + second term
    current_term = first_term + second_term
    # Print out current term 
    cat(current_term)
    # Exit Loop when Accumulated reaches indicated limit or greater
    if (accumulated_sum >= sum_limit) {
      cat("\n")
      break
    } else { # add command to output 
      cat(" , ")
    }
    # Advancing, first term set set to value of second term 
    first_term = second_term
    # current term beocomes second term 
    second_term = current_term
    # add to accumulated sum 
    accumulated_sum <- accumulated_sum + current_term
    
  }
}

#' Runner Function
#'
#' Demonstrates the usage of `fibonacci_function()` by calling it accumulated value limit, 1000.
runner_function <- function() {
  fibonacci_function(1000)
}

runner_function()
```

---

### Q3: Functions and Data Manipulation

- **a)** Write a function `calculate_mean_sd()` that takes a numeric vector and returns a **list** containing its **mean** and **standard deviation**.

    ``` r
    calculate_mean_sd <- function(...) { # Take in any vector of any value types 
    input_values <- c(...) # assign to a local variable
    
    # validate data type 
    if (!is.numeric(input_values)) {
      cat("Invalid Input Type!" , "\n")
      return() #exit 
    }
    
    #calculate standard deviation skipping any empty (na.rm)
    standard_dev <- sd(input_values, na.rm = TRUE)
    
    #calculate mean 
    average_value <- mean(input_values)
    
    #construct result list 
    result_list <- c(sd_value = standard_dev, average_value = average_value)
    return(result_list)
  }
  
  # Happy case 
  runner_function_normal_operation <- function() {
    results_list <- calculate_mean_sd(10, 2, 4, 5, 6, 7, 8, 11, 12, 13)
    
    # Not null then 
    if (length(results_list) > 0) {
      
      # Print out Structure 
      cat("structure: ")
      str(results_list)
      
      # Print out mean then follows by Standard Deviation 
      cat(
        "\n",
        "result_list contains: ",
        "average :",
        results_list[['average_value']],
        " standard deviation: ",
        results_list[['sd_value']]
      )
    }
  }
  
  runner_function_normal_operation()
  
  # Testing invalid input in this case string. 
  runner_function_error <- function() {
    results_list <- calculate_mean_sd("test 1", "test 2")
    
    if (length(results_list) > 0) {
      cat("structure: ")
      str(results_list)
      cat(
        "\n",
        "result_list contains: ",
        "average :",
        results_list[['average_value']],
        " standard deviation: ",
        results_list[['sd_value']]
      )
    }
  }
  
  runner_function_error()
  ```

- **b)** Write a function `filter_data()` that accepts:
  - a **data frame**,  
  - a **column name**, and  
  - a **threshold** value.  
  It should return a filtered data frame with rows where the column value exceeds the threshold.
``` r
# filter data function takes in a data frame, required column and threshold
filter_data <- function (d_frame, required_column, threshold) {
  if (!is.data.frame(d_frame)) {
    cat("This requires Data Frame to proceed!")
    return()
  }
  # filter levels exceeding threshold only
  result <- d_frame[d_frame[[required_column]] > threshold, ]
  return(result)
}

# Runner function contains sample data
# This case study was selected because it fulfills requirement in the prompt
# filtering data exceeding threshold.
# In this HESA is only interested in "university students" so any students
# enrolled in any levels below 7 will be excluded from HESA statistics
runner_function_hesa <- function() {
  students_levels <- data.frame (
    "Name" = c(
      "Ernie",
      "Marc",
      "Laura",
      "Jen",
      "Angus",
      "Reid",
      "Tyler",
      "Taylor",
      "Ankita",
      "Attisha"
    ),
    "SCQF" = c(5, 5, 6, 6, 7, 7, 8, 9, 11, 11)
  )
  
  
  result <- filter_data(students_levels, "SCQF", 6)
  print(result)
  
}
runner_function_hesa() 
```
---

### Q4: Data Manipulation and Analysis with `mtcars`

Using R’s built-in `mtcars` dataset:

- **a)** Identify the cars with the **highest** and **lowest** `mpg` (miles per gallon).
``` r
  library(tidyverse)

  mtcars_lowest_mpg <- function () {
    #Sort by MPG in ascending order 
    ascending_list <- mtcars[order(mtcars$mpg), ]
    #Select the first one from the sorted list 
    head(ascending_list, 1)
  }

  mtcars_highest_mpg <- function () {
    #Sort by MPG in aescending order 
    descending_list  <- mtcars[order(-mtcars$mpg), ]
    #Select the first one from the sorted list 
    head(descending_list, 1)
  }

  #Print out information here
  runner <- function () {
    cat("\n")
    cat("Car with highest MPG (most fuel efficient): ", "\n")
    print(mtcars_highest_mpg())
    cat("\n")
    cat("Car with lowest MPG (least fuel efficient): ", "\n")
    print(mtcars_lowest_mpg())
  }

  runner()
```   
- **b)** Calculate the **average weight (`wt`)** for cars grouped by number of cylinders (`cyl`).  
``` r
  library(tidyverse)
  
  #import mtcars as a data frame
  data(mtcars)
  
  average_weight <- function() {
    #convert cylinder counts into factor
    mtcars$cyl <- as.factor(mtcars$cyl)
    #calculate average 
    average_weights <- tapply(mtcars$wt, mtcars$cyl, mean)
    #prepare formatted output
    labels <- sprintf("%s cylinders: %.2f lbs", names(average_weights*1000), average_weights)
    return(labels)
  }
  runner <- function() {
    cat("Average Weights:", "\n")
    cat(average_weight(), "\n")
  }
  
  runner()
```
- Hint: Consider using `tapply()` for a concise solution._

---

### Q5: Data Visualization

Use the provided script [`Generate-data-1.R`](Generate-data-1.R) to generate your dataset.

``` r
# For the scatter-plot, you can use this code to generate the data:
set.seed(1)
x <- rnorm(100)
y <- x^3 + rnorm(100)

# And for the box-plot, you can use this code to generate the data:
set.seed(1)
data <- list(
  Group1 = rnorm(100),
  Group2 = rnorm(100, mean = 2),
  Group3 = rnorm(100, mean = 1.5)
)
```

- **a)** Write your own R code to generate a **scatter plot** matching the one linked in the course materials.

### Answer

![scatter plot](assets/scatter-plot-1.png)

``` r 
library(ggplot2)

#' Generate Random Scatter Data
#'
#' This function generates a data frame of 100 points with normally distributed `x` values
#' and corresponding `y` values computed as `x^3 + noise`.
#'
#' @param seed_value Integer seed for reproducibility of the random number generator.
#'
#' @return A data frame with two columns: \code{x_values} and \code{y_values}.
#'
#' @examples
#' generate_scatter_data(123)
generate_scatter_data <- function(seed_value) {
  set.seed(seed_value)
  x <- rnorm(100)
  y <- x^3 + rnorm(100)
  result <- data.frame(x_values = x, y_values 
                       = y)
  return(result)
}

#' Run Scatter Plot Generator and Plot
#'
#' This function runs the scatter data generator with a fixed seed,
#' displays a summary of the data, and plots the scatter plot using ggplot2.
#'
#' @return A ggplot2 scatter plot object (and prints it to the active graphics device).
#'
#' @examples
#' runner()

runner <- function() {
  scatter_data <- generate_scatter_data(1);
  summary(scatter_data)
  ggplot(
    data = scatter_data,
    mapping = ( aes(x = x_values, y = y_values)) 
  ) + geom_point()

}
runner()
```

![box plot](assets/scatter-plot-answer.png)

- **b)** Write your own R code to generate a **box plot** matching the one linked in the course materials.

![box plot](assets/box-plot.png)

### Answer

``` r 
library(ggplot2)
library(tidyr)
library(dplyr)

generate_box_plot_data <- function (seed_value) {
  set.seed(seed_value)
  results <- data.frame(
    Group1 = rnorm(100),
    Group2 = rnorm(100, mean = 2),
    Group3 = rnorm(100, mean = 1.5)
  )
  return(results)
}

box_plot_function <- function() {
  data <- generate_box_plot_data(1)
  data_long_values <- data%>% 
    pivot_longer(cols = everything(), names_to = "Group", values_to = "Value")
  ggplot(data_long_values, aes(x = Group, y = Value)) + geom_boxplot(fill = "blue") + theme_minimal() + labs(title = "Boxplot (3 Groups)", x = "Group", y = "Value")
}

runner <- function() {
  box_plot_function()
}

runner()
```

![box plot](assets/box-plot-answer.png)

---

## Submission Guidelines

1. Submit a **well-structured report** containing:
   - Clear explanations
   - R code (as **plain text**, not screenshots)
   - Any additional screenshots or outputs if helpful

2. Submit by **email** to:  
   📧 `weeklyclasses@conted.ox.ac.uk`

3. Attach your **Declaration of Authorship** form as per the student handbook.

---

## Tips & Resources

- Use the course materials, R documentation, and trusted online tutorials.
- Practice reproducible coding with comments and structured functions.
- Format your report professionally with sections, headings, and explanations.

---

## Good Luck

This assignment is a chance to test and apply your learning. Focus on clarity, accuracy, and showcasing your understanding of R.

## References

- DataCamp (2025) Creating a named list. Available at: [DataCamp](https://www.datacamp.com/tutorial/creating-lists-r) (Accessed: 30 May 2025).

- DataCamp (2025) *Sorting in R*. Retrieved June 3, 2025, from [DataCamp](https://www.datacamp.com/doc/r/sorting) [Accessed: June 3, 2025].

- DataCamp (2024) *Subsetting in R Tutorial*. Available at: [DataCamp](https://www.datacamp.com/tutorial/subsets-in-r) (Accessed: 30 May 2025).

- Hadley, W. (2025) R for Data Science (2e). Available at: [Hadley](https://r4ds.hadley.nz/data-visualize.html) (Accessed: 4 June 2025), Section: Data visualization.

- Hadley, W. (2025) R for Data Science (2e). Available at: [Hadley](https://r4ds.hadley.nz/numbers.html#numeric-summaries) (Accessed: 26 May 2025), Section: Numeric Transformations.

- Matloff, N. (2011) The Art of R Programming. No Starch Press. Available at: [Matloff](https://learning.oreilly.com/library/view/the-art-of/9781593273842/ch02s06.html#vector_in_comma_vector_out) (Accessed: 26 May 2025), Section: Vectorized Operations.

- Matloff, N. (2025) The Art of R Programming, Section: Introduction to Functions. No Starch Press. Available at: [Matloff](https://learning.oreilly.com/library/view/the-art-of/9781593273842/ch01s03.html) (Accessed: 28 May 2025).
