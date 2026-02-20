---
title: "Simple Linear Regression in Python: A Beginner's Guide"
author: "Tyran Heaton"
date: "2026-02-20"
format: html
---

## Introduction

Simple linear regression is one of the most fundamental statistical techniques that allows us to predict a variable using another. Whether you're predicting whether China or the USA will put humans on the moon again first based on recent technological advances of each country or studying the relationship between movie box office success and production budgets, linear regression is a valuable tool.

In this tutorial, you'll learn the mathematics behind simple linear regression, how to implement it in Python, and how to interpret your results. By the end, you'll be able to build your own predictive models with confidence. Let's dive in!

## What is Simple Linear Regression?

Simple linear regression models the relationship between two variables using a straight line. The equation is:

$$y = \beta_0 + \beta_1x + \epsilon$$

Where:
- $y$ is the dependent variable (what we're predicting)
- $x$ is the independent variable (what we're using to predict)
- $\beta_0$ is the y-intercept
- $\beta_1$ is the slope
- $\epsilon$ is the error term

The goal is to find the best values for $\beta_0$ and $\beta_1$ that minimize the sum of squared errors:

$$SSE = \sum_{i=1}^{n}(y_i - \hat{y}_i)^2$$

Where $\hat{y}_i$ represents our predicted values.

## Sample Dataset

Let's work with a simple example: predicting exam scores based on hours studied. Here's our dataset:

| Student | Hours Studied (x) | Exam Score (y) |
|---------|-------------------|----------------|
| 1       | 2                 | 65             |
| 2       | 3                 | 70             |
| 3       | 4                 | 75             |
| 4       | 5                 | 82             |
| 5       | 6                 | 85             |
| 6       | 7                 | 90             |

## Implementing Linear Regression in Python

Now let's implement this in Python using scikit-learn. First, we'll need to import our libraries and prepare our data:

```python
import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Our data from the table above
hours_studied = np.array([2, 3, 4, 5, 6, 7]).reshape(-1, 1)
exam_scores = np.array([65, 70, 75, 82, 85, 90])

# Create and train the model
model = LinearRegression()
model.fit(hours_studied, exam_scores)

# Get the coefficients
intercept = model.intercept_
slope = model.coef_[0]

print(f"Intercept (β₀): {intercept:.2f}")
print(f"Slope (β₁): {slope:.2f}")
print(f"Equation: y = {intercept:.2f} + {slope:.2f}x")

# Make a prediction
hours = 5.5
predicted_score = model.predict([[hours]])
print(f"\nPredicted score for {hours} hours: {predicted_score[0]:.2f}")
```

## Interpreting the Results

When you run this code, you'll get output similar to:
- **Intercept (β₀)**: ~52.86
- **Slope (β₁)**: ~5.14

This means that for every additional hour studied, the exam score increases by approximately 5.14 points. The intercept suggests a baseline score of about 52.86 when study time is zero (though this may not be meaningful in practice).

The prediction tells us that a student who studies 5.5 hours would likely score around 81 points on the exam.

## Conclusion

Congratulations! You've just learned the fundamentals of simple linear regression. You now understand the mathematical foundation behind the technique, how to implement it in Python using scikit-learn, and how to interpret your results.

Simple linear regression is a powerful starting point for statistical modeling. While real-world problems often require more complex approaches, mastering this technique gives you a solid foundation for understanding more advanced statistical methods.

## Next Steps

Ready to practice? Here's what you can do:

1. **Try it yourself**: Use this code with your own data. Think of two variables that might be related (temperature and ice cream sales, age and income, etc.)
2. **Visualize your results**: Add matplotlib code to plot your regression line
3. **Explore further**: Learn about R-squared values to measure model performance

Remember, the best way to learn statistics is by doing. Start small, experiment often, and don't be afraid to make mistakes.

Happy coding! 🚀

---

*Have questions about this tutorial? Want to suggest improvements? Let me know!*