# computational_statistics_4

# Sample Data
muestra_A <- c(79.98, 80.04, 80.02, 80.04, 80.03, 80.03, 80.04, 79.97,
               80.05, 80.03, 80.02, 80.00, 80.02)
muestra_B <- c(80.02, 79.94, 79.98, 79.97, 79.97, 80.03, 79.95, 79.97)

# a) Box plot and Quantile-Quantile plot
boxplot(muestra_A, muestra_B, names = c("Sample A", "Sample B"), 
        col = c("blue", "red"), main = "Sample Comparison")
qqplot(muestra_A, muestra_B, main = "Quantile-Quantile Plot")

# b) Test for equality of variances
# We will use Bartlett's test to compare the variance of both samples.
result_var <- bartlett.test(list(muestra_A, muestra_B))
if (result_var$p.value < 0.05) {
    cat("Bartlett's test rejects the equality of variances.\n")
} else {
    cat("Bartlett's test does not reject the equality of variances.\n")
}

# c) Test for equality of means
# We will use Student's t-test to compare the means of both samples.
result_t <- t.test(muestra_A, muestra_B)
if (result_t$p.value < 0.05) {
    cat("Student's t-test rejects the equality of means.\n")
} else {
    cat("Student's t-test does not reject the equality of means.\n")
}
