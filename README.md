# 📘 R Programming for Data Science: Introduction  
## 📝 Formative Assignment (Non-graded)

**Due Date:** 5 June 2025, 5:59 AM  
**Release Date:** 19 May 2025, 6:00 AM  
**Submission Format:** Word Document or PDF  
**Submission Method:** Email to `weeklyclasses@conted.ox.ac.uk`  
**Attach:** Completed Declaration of Authorship form

---

## 📂 Overview

This formative assignment is designed to help you consolidate key concepts in R programming, including vectorization, control flow, function writing, data manipulation, and basic visualization. You are encouraged to reference course materials and seek additional learning resources if needed.

---

## ✅ Assignment Questions

### Q1: R Programming Concepts

Answer each question in **no more than 60 words**:

- **a)** What is vectorization in R, and what are its benefits?

   Vectorisation is an implicit process in R where an operation can be peformed on each elements of a vector.
  A benefit of vecitorisation is that the code becomes more readable because there is no need to explicitly loop over elements of vector.
  for example two vectors can added together or a numerical value can be muliplied for all the vector values.
  
- **b)** What is recycling in R? Provide an example.  
- **c)** What is operator precedence? Provide an R example.  
- **d)** What is function scope, and why is it important?

---

### Q2: Control Flow and Looping

- **a)** Write an R function `fibonacci(n)` that returns the first `n` Fibonacci numbers as a vector.  
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
<img width="1060" alt="scatter-plot-1" src="https://github.com/user-attachments/assets/99317545-3662-4c68-b407-832589633594" />
- **b)** Write your own R code to generate a **box plot** matching the one linked in the course materials.
<img width="820" alt="box-plot" src="https://github.com/user-attachments/assets/5bdd49c6-d1f6-4236-b546-a6e3dad7f312" />
---


## 📤 Submission Guidelines

1. Submit a **well-structured report** containing:
   - Clear explanations
   - R code (as **plain text**, not screenshots)
   - Any additional screenshots or outputs if helpful

2. Submit by **email** to:  
   📧 `weeklyclasses@conted.ox.ac.uk`

3. Attach your **Declaration of Authorship** form as per the student handbook.

---

## 🧠 Tips & Resources

- Use the course materials, R documentation, and trusted online tutorials.
- Practice reproducible coding with comments and structured functions.
- Format your report professionally with sections, headings, and explanations.

---

## 🎓 Good Luck!

This assignment is a chance to test and apply your learning. Focus on clarity, accuracy, and showcasing your understanding of R.
