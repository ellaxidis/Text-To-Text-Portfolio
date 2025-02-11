🤖 **Qwen AI**

---

## 📌 **Role: Programmer**

📝 **Task: Write Python code to analyze Apple's sales data over the last five years (2020-2025)**

---

# Program of a Analyzing Sales "Apple" Over the Last Five Years
To write the code, we will follow the software development process, starting with requirements analysis and ending with product creation. The process includes several key steps: data analysis, using libraries for processing (NumPy and Pandas), identifying patterns (seasonality, trends, anomalies), and presenting results in charts and tables.

**Here is an example of a structured Python program that meets the specified requirements:**

```python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Loading data from a CSV file
def load_data(filepath):
    """
    Function to load data from a file.
    :param filepath: Path to the data file
    :return: DataFrame with data
    """
    data = pd.read_csv(filepath)
    return data

# Preprocessing data
def preprocess_data(data):
    """
    Data preprocessing: removing missing values, converting data types.
    :param data: Raw data
    :return: Processed data
    """
    # Convert date to datetime format
    data['Date'] = pd.to_datetime(data['Date'])
    # Remove rows with missing values
    data.dropna(inplace=True)
    return data

# Analyzing trends
def analyze_trends(data):
    """
    Analyze sales trends over time.
    :param data: Data for analysis
    :return: DataFrame with trends
    """
    # Grouping data by year and month to identify trends
    trends = data.groupby([data['Date'].dt.year, data['Date'].dt.month])['Sales'].mean()
    return trends

# Detecting seasonality
def analyze_seasonality(data):
    """
    Identify seasonal fluctuations in sales.
    :param data: Data for analysis
    :return: DataFrame with seasonality
    """
    # Grouping data by month to analyze seasonality
    seasonality = data.groupby(data['Date'].dt.month)['Sales'].mean()
    return seasonality

# Detecting anomalies
def detect_anomalies(data):
    """
    Identify anomalies in the data.
    :param data: Data for analysis
    :return: List of anomalous points
    """
    mean = np.mean(data['Sales'])
    std_dev = np.std(data['Sales'])
    anomalies = data[(data['Sales'] > mean + 3 * std_dev) | (data['Sales'] < mean - 3 * std_dev)]
    return anomalies

# Visualizing results
def plot_results(trends, seasonality, anomalies):
    """
    Plot graphs for trends, seasonality, and anomalies.
    :param trends: Sales trends
    :param seasonality: Seasonal sales fluctuations
    :param anomalies: Anomalies in the data
    """
    fig, ax = plt.subplots(3, 1, figsize=(10, 15))
    # Trends graph
    trends.plot(ax=ax[0], title='Sales Trends', ylabel='Average Sales')
    # Seasonality graph
    seasonality.plot.bar(ax=ax[1], title='Seasonal Sales Fluctuations', ylabel='Average Sales')
    # Anomalies graph
    ax[2].scatter(anomalies['Date'], anomalies['Sales'], color='red')
    ax[2].set_title('Anomalies in Sales')
    ax[2].set_ylabel('Sales')
    plt.tight_layout()
    plt.show()

# Main function
def main():
    # Path to the data file
    filepath = 'apple_sales_data.csv'
    # Load and preprocess data
    data = load_data(filepath)
    data = preprocess_data(data)
    # Analyze data
    trends = analyze_trends(data)
    seasonality = analyze_seasonality(data)
    anomalies = detect_anomalies(data)
    # Output results in table form
    print("Trends Table:")
    print(trends)
    print("\nSeasonality Table:")
    print(seasonality)
    print("\nAnomalies Table:")
    print(anomalies)
    # Visualize results
    plot_results(trends, seasonality, anomalies)

if __name__ == "__main__":
    main()
```

This code demonstrates the software development process where each component is well-documented and logically separated, making it easy to read and maintain. The program uses NumPy and Pandas libraries for data analysis and matplotlib for visualizing results.

*Note: All data presented is exclusively for informational purposes and does not constitute official financial reporting for Apple.*

---

## 📌 **Role: UX/UI Designer**

📝 **Task: Create a mobile app mockup for an online clothing store**

---

# Mockup of a Mobile App for an Online Clothing Store

## Home Screen (Main Page)
| Header         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Logo**       | Positioned at the top left. Simple and minimalist style                     |
| **Search Bar** | Centered at the top. A simple rectangle with a search icon                   |
| **Categories** | Horizontal scroll bar with product categories                               |
| **Banner**     | Smooth animation cycling through current offers or new arrivals             |

## Navigation Menu
| Icon  | Name       | Description                                                |
|-------|------------|------------------------------------------------------------|
| 🏠    | Home       | Leads back to the main page                                |
| 🔍    | Search     | Opens the advanced search functionality                     |
| 💬    | Chat       | Accesses customer support or chat                          |
| 🛒    | Cart       | Displays selected items                                    |
| 📱    | Profile    | Provides access to account settings and order history      |

## Category Screen
| Header         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Category Name** | Large text highlighted in pastel colors                                   |
| **Product List**  | Cards displaying product images, names, and prices                        |
| **Filters**      | Drop-down menu for sorting by size, color, and price                       |

## Product Screen
| Header         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Image**      | Large product image with zoom capability                                    |
| **Description**| Brief product description, materials, and care instructions                 |
| **Price**      | Clearly displayed with an "Add to Cart" button                               |
| **Sizes**      | Size selection via circular buttons                                          |

## Cart
| Header         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **List**       | Displays all added items with removal options                               |
| **Total**      | Shows total order amount with a "Proceed to Checkout" button                |

## Profile
| Header         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Information**| User personal details                                                       |
| **Orders**     | Order history with filters by status                                        |
| **Settings**   | Options to change password, notifications, and other parameters             |

### Color Palette
- Main Background: White (#FFFFFF)
- Accents: Soft Blue (#AED9E0), Light Green (#C5E1A5)
- Text: Dark Gray (#424242)

### Notes
- All control elements are placed at the bottom of the screen for one-handed use.
- Minimalism is used in design to create a sense of lightness and freshness.

This mockup is created considering modern UI/UX design trends in 2025, such as minimalism, ease of use, and aesthetic presentation.

---

&copy; 2025 Elizaveta Teplyashina. All materials are completely original and used for informational purposes only. 18+
