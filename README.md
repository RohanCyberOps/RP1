

# 📊 **SBUX Monthly Returns Analysis** 📈

## Overview

This project performs an analysis of Starbucks (SBUX) stock returns using R. The analysis includes both **simple returns** and **continuously compounded returns (CC returns)** for a period of one month. It also calculates the **growth of $1 invested in SBUX** and provides visual insights through various plots.

---

## 🔧 **Features**

- **Simple Returns Calculation**: Calculate simple monthly returns for SBUX.
- **Continuously Compounded Returns**: Convert simple returns to continuously compounded returns.
- **Visualization**: Plot both simple and CC returns on separate graphs and compare them on the same graph.
- **Investment Growth**: Compute the future value of a $1 investment in SBUX.
- **Probabilistic Analysis**: Visualize discrete probability distributions and cumulative distribution functions (CDF).

---

## 💻 **Prerequisites**

Ensure you have R installed along with the necessary libraries:

```R
install.packages("psych")
```

---

## 📊 **Code Walkthrough**

### **1. Compute Returns**
We calculate the **simple returns** for Starbucks and then convert them into **continuously compounded returns**.

```R
# Simple Returns
sbux.ret = (sbuxPrices.df[2:n,1] - sbuxPrices.df[1:(n-1),1])/sbuxPrices.df[1:(n-1),1]

# Continuously Compounded Returns
sbux.ccret = log(1 + sbux.ret)
```

### **2. Visualization of Returns**
We split the screen into two plots: one for simple returns and another for CC returns. 

```R
# Plotting Simple and CC Returns
par(mfrow=c(2,1))  # Set up plot area

plot(sbux.ret, type="l", col="blue", lwd=2, ylab="Return", main="Monthly Simple Returns on SBUX")
abline(h=0)

plot(sbux.ccret, type="l", col="blue", lwd=2, ylab="Return", main="Monthly Continuously Compounded Returns on SBUX")
abline(h=0)

par(mfrow=c(1,1))  # Reset to a single plot
```

### **3. Growth of $1 Investment**
Next, we calculate how a $1 investment in SBUX would grow over time.

```R
# Compute Gross Returns
sbux.gret = 1 + sbux.ret

# Calculate Future Values
sbux.fv = cumprod(sbux.gret)
```

### **4. Probability and Distribution Analysis**
We visualize discrete probability distributions and compute cumulative distribution functions (CDF).

```R
# Probability Distribution for Microsoft Returns
r.msft = c(-0.3, 0, 0.1, 0.2, 0.5)
prob.vals = c(0.05, 0.20, 0.50, 0.20, 0.05)

barplot(prob.vals, names.arg = as.character(r.msft), xlab="Return")
title("Annual Return on Microsoft")

# Plot CDF of Discrete Distribution
cdf = c(0, 0.05, 0.25, 0.75, 0.95, 1)
x.vals = c(-0.4, -0.3, 0, 0.1, 0.2, 0.5)
plot(x.vals, cdf, lwd=4, type="S")
```

---

## 🛠️ **Functions and Packages Used**

- **read.csv()**: Read data from CSV files.
- **log()**: Calculate the logarithm for continuous compounding.
- **par()**: Adjust the plotting area for multiple plots.
- **cumprod()**: Calculate cumulative product for future value.
- **barplot() & plot()**: Visualize the data.

---

## 📝 **Author**

- **Name**: E. Zivot
- **Date**: Created on September 24, 2009
- **Last Updated**: June 27, 2011

---

## 📚 **Further Reading**

For more information on the R functions used, refer to the official R documentation:

- [R Read CSV](https://www.rdocumentation.org/packages/utils/versions/latest/topics/read.csv)
- [R log function](https://www.rdocumentation.org/packages/base/versions/latest/topics/log)

---

## 📈 **Visualizations**

The following graphs provide a comprehensive visual representation of SBUX stock performance:

- **Simple Monthly Returns** 📊
- **Continuously Compounded Returns** 📉
- **Investment Growth Over Time** 📈

---

## 🚀 **Conclusion**

This analysis offers insights into SBUX stock performance over the analyzed period. The different return calculations and visualizations help compare investment scenarios.
