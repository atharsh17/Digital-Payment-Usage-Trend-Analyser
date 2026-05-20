# Digital-Payment-Usage-Trend-Analyser
A Digital Payment Usage Trend Analyser examines transaction patterns, user behavior, seasonal changes, and platform preferences, providing insights to optimize services, enhance security, forecast demand, and support data-driven financial decision-making effectively.

Program Code:
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv('payments.csv')

# Convert date column to datetime
data['date'] = pd.to_datetime(data['date'])

# 1. Total transactions per day
daily_transactions = data.groupby('date').size()

# 2. Total amount spent per day
daily_amount = data.groupby('date')['amount'].sum()

# 3. Payment method usage count
method_usage = data['method'].value_counts()

# 4. Average transaction amount per method
avg_amount_method = data.groupby('method')['amount'].mean()

print("Daily Transactions:\n", daily_transactions)
print("\nDaily Amount Spent:\n", daily_amount)
print("\nPayment Method Usage:\n", method_usage)
print("\nAverage Amount per Method:\n", avg_amount_method)

# Plot daily transaction trend
plt.figure()
daily_transactions.plot()
plt.title('Daily Transaction Count')
plt.xlabel('Date')
plt.ylabel('Number of Transactions')
plt.show()

# Plot daily amount trend
plt.figure()
daily_amount.plot()
plt.title('Daily Transaction Amount')
plt.xlabel('Date')
plt.ylabel('Total Amount')
plt.show()

# Plot method usage
plt.figure()
method_usage.plot(kind='bar')
plt.title('Payment Method Usage')
plt.xlabel('Method')
plt.ylabel('Count')
plt.show()