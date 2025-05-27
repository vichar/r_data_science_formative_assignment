# R Programming for Data Science: Introduction  
## Formative Assignment (Non-graded)

**Due Date:** 5 June 2025, 5:59 AM  
**Release Date:** 19 May 2025, 6:00 AM  
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
  - Operator precedence in computer science simply means the order which mathematical and logical operations are to be performed
  - One notable exception any operation in side brackets are performed first from left to right
  - Examples in R
    This example 3 * 3 is performed before any additions according to order of precedence
  ```
    ``` r
    > a <- 3 * 3 + 2
    > cat("a: ", a)
    a:  11
    ```
    This example 3 + 2 is performed due to ( ) has higher precedence than
    multiplication
    ``` r
    > b <- 3 * (3 + 2)
    > cat ("b: ", b)
    b:  15
    > 
- **d)** What is function scope, and why is it important?
  ```
  - Scope denotes the visibility or accessibility of variables and functions.
  - Variables defined in the global or higher scope will be visible within any function defined within the script.
  - Variables or functions defined within a function will only be visible within that function's scope.
  - In the event of naming conflict, the definition and assignment within the function's scope takes precedence over higher scopes, including global scope.
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

---

### Q3: Functions and Data Manipulation

- **a)** Write a function `calculate_mean_sd()` that takes a numeric vector and returns a **list** containing its **mean** and **standard deviation**.  
- **b)** Write a function `filter_data()` that accepts:
  - a **data frame**,  
  - a **column name**, and  
  - a **threshold** value.  
  It should return a filtered data frame with rows where the column value exceeds the threshold.

---

### Q4: Data Manipulation and Analysis with `mtcars`

Using R’s built-in `mtcars` dataset:

- **a)** Identify the cars with the **highest** and **lowest** `mpg` (miles per gallon).  
- **b)** Calculate the **average weight (`wt`)** for cars grouped by number of cylinders (`cyl`).  
  _Hint: Consider using `tapply()` for a concise solution._

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

<img width="1000" alt="scatter-plot-1" src="https://github.com/user-attachments/assets/99317545-3662-4c68-b407-832589633594" />

- **b)** Write your own R code to generate a **box plot** matching the one linked in the course materials.

<img width="1000" alt="box-plot" src="https://github.com/user-attachments/assets/5bdd49c6-d1f6-4236-b546-a6e3dad7f312" />


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

##  Good Luck!

This assignment is a chance to test and apply your learning. Focus on clarity, accuracy, and showcasing your understanding of R.


## References
Matloff, N. (2011) The Art of R Programming, No Starch Press. Available at: https://learning.oreilly.com/library/view/the-art-of/9781593273842/ch02s06.html#vector_in_comma_vector_out [Accessed 26 May 2025], Section: Vectorized Operations.
Hadley, W. (2025) R for Data Science (2e). Available at: https://r4ds.hadley.nz/numbers.html#numeric-summaries [Accessed 26 May 2025], Section: Numeric Transformations.
