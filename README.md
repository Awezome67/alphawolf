import matplotlib.pyplot as plt
import numpy as np
import scipy.stats as stats

# Define the mean and standard deviation
mean = 75  # Assume mean score is 75
std_dev = 10  # Assume standard deviation is 10

# Define the Empirical Rule percentages
empirical_percentages = {
    "1 Std Dev": 68,
    "2 Std Dev": 95,
    "3 Std Dev": 99.7
}

# Calculate the ranges
one_std_range = (mean - std_dev, mean + std_dev)
two_std_range = (mean - 2*std_dev, mean + 2*std_dev)
three_std_range = (mean - 3*std_dev, mean + 3*std_dev)

# Generate x values for the normal curve
x = np.linspace(mean - 4*std_dev, mean + 4*std_dev, 1000)
y = stats.norm.pdf(x, mean, std_dev)

# Plot the normal distribution
plt.figure(figsize=(10, 6))
plt.plot(x, y, label='Normal Distribution', color='blue')

# Highlighting the empirical rule ranges
plt.fill_between(x, y, where=(x >= one_std_range[0]) & (x <= one_std_range[1]), color='yellow', alpha=0.5, label='68% within 1 Std Dev')
plt.fill_between(x, y, where=(x >= two_std_range[0]) & (x <= two_std_range[1]), color='orange', alpha=0.5, label='95% within 2 Std Dev')
plt.fill_between(x, y, where=(x >= three_std_range[0]) & (x <= three_std_range[1]), color='red', alpha=0.3, label='99.7% within 3 Std Dev')

# Labels and title
plt.title("Empirical Rule (68-95-99.7) for Normal Distribution of Scores")
plt.xlabel("Scores")
plt.ylabel("Probability Density")
plt.legend()
plt.grid()
plt.show()

# Explanation
print("The Empirical Rule states that for a normal distribution:")
print(f"- About {empirical_percentages['1 Std Dev']}% of students scored between {one_std_range[0]:.2f} and {one_std_range[1]:.2f}.")
print(f"- About {empirical_percentages['2 Std Dev']}% of students scored between {two_std_range[0]:.2f} and {two_std_range[1]:.2f}.")
print(f"- About {empirical_percentages['3 Std Dev']}% of students scored between {three_std_range[0]:.2f} and {three_std_range[1]:.2f}.")
