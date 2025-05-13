![Uploading image.png…]()


# Sales Report Dashboard


## Introduction

The Sales Report dashboard is a powerful tool designed to deliver insights into sales performance across various cities and product categories. By employing data visualization techniques, it transforms complex sales data into an accessible and actionable format, empowering stakeholders to make informed decisions based on revenue and quantity metrics.

**Sales Performance Report**

**Overview** This Power BI model delivers a consolidated view of customer orders, product performance, and revenue metrics. It is designed to help analysts and stakeholders track sales trends, top-selling products, customer distribution, and overall business performance.

---

### Data Sources

* **Customers**: Contains customer demographic and geographic information.
* **Products**: Lists the company's product catalog with categories and identifiers.
* **Orders**: Transactional order data capturing order dates, quantities, and sales revenue.

---

### Data Model Structure

![Screenshot (94)](https://github.com/user-attachments/assets/be713b7b-c919-44d0-a92d-cb7df1bc5b77)


The model consists of three tables with one-to-many relationships:

```text
Customers (1) ———< Orders >——— (1) Products
                 
Relationships:
- Customers[CustomerID] → Orders[CustomerID]
- Products[ProductID] → Orders[ProductID]
```

* **Customers**

  * City
  * CountryRegion
  * CustomerID
  * Name
  * PostalCode

* **Products**

  * Category
  * ProductID
  * ProductName

* **Orders**

  * CustomerID
  * OrderDate
  * OrderItemID
  * ProductID
  * Quantity   *(Aggregated as ****\`\`****)*
  * Revenue    *(Aggregated as ****\`\`****)*

---

### Measures & Calculations

* **Total Quantity Sold**: `SUM(Orders[Quantity])`
* **Total Revenue**: `SUM(Orders[Revenue])`
* **Average Order Value**: `DIVIDE([Total Revenue], DISTINCTCOUNT(Orders[OrderItemID]))`
* **Orders by Region**: Custom DAX measure filtering by `Customers[CountryRegion]`.

Feel free to extend with additional measures such as month-over-month growth, product category breakdowns, and customer segmentation metrics.

---

### Visualizations

Use this model to build reports and dashboards, such as:

* Time series charts of revenue and quantity trends.
* Map visual showing sales distribution by city or region.
* Bar charts of top products by revenue or units sold.
* Customer insights by segment or geography.

---

### Setup & Refresh

1. Connect to your data sources (e.g., Excel, SQL Server, CSV) and load the three tables.
2. Verify data types and relationships as defined above.
3. Configure scheduled refresh settings in Power BI Service to keep data up to date.

---

### Contributors

* *Model design and DAX authored by Abdelrhman Salem*

---

*For questions or collaboration, reach out to the BI team or submit an issue in the project repository.*

## Visualizations

The dashboard comprises four key visualizations, each offering a unique perspective on the sales data:

### 1. Sum of Revenue by City
- **Type**: Horizontal bar chart
- **Description**: Illustrates the total revenue generated across different cities, with the x-axis ranging from $0K to $150K and the y-axis listing cities.
- **Details**: 
  - London leads with revenue nearing $150K.
  - Woolston follows, with slightly less revenue.
  - Union City, Liverpool, Fullerton, and Gloucestershire show progressively lower revenues, with Gloucestershire at the bottom.
- **Purpose**: Highlights top-performing cities by revenue.

### 2. Sum of Quantity by Category
- **Type**: Pie chart
- **Description**: Displays the distribution of sales quantities across product categories, with each segment color-coded and labeled with percentages.
- **Details**: 
  - Touring Bikes: ~22.11% (largest share).
  - Other notable categories: Jerseys (~2.49%), Road Bikes (~2.49%), Mountain Bikes (~2.64%), Mountain Frames (~2.64%), Helmets (~2.73%), Vests (~2.87%), Pedals (~3.16%), Shorts (~3.83%).
  - Smaller segments range up to ~12.8%.
  - Note: The total quantity sum of 222 (10.64%) may reflect a subset; refer to data labels for accuracy.
- **Purpose**: Identifies the most sold product categories by quantity.

### 3. Sum of Revenue by Category
- **Type**: Vertical bar chart
- **Description**: Shows total revenue per product category, with the y-axis ranging from $0M to $2M.
- **Details**: 
  - Top earners: Mountain Bikes, Road Bikes, and Touring Bikes, each nearing $2M.
  - Moderate earners: Helmets, Jerseys, Shorts (~$1M or less).
  - Low earners: Bottles and Cages, Brakes, Caps, Cleaners, etc., near $0M.
- **Purpose**: Pinpoints the highest revenue-generating product categories.

### 4. Sum of Revenue by City (Map)
- **Type**: World map with markers
- **Description**: Visualizes revenue by city using circular markers, where size correlates with revenue amount, focusing on North America and Europe.
- **Details**: 
  - North America: Cluster in the western U.S. (e.g., California).
  - Europe: Prominent marker in the U.K. (likely London), with smaller markers nearby.
  - Africa: Minor presence, less emphasized.
- **Purpose**: Reveals geographic revenue distribution.

## Key Findings

- **Top City**: London dominates in revenue generation.
- **Quantity Leader**: Touring Bikes lead in sales volume.
- **Revenue Champions**: Mountain Bikes, Road Bikes, and Touring Bikes drive the highest revenue.
- **Geographic Trends**: Revenue concentrates in the western U.S. and the U.K., suggesting key markets.

## Usage Instructions

To effectively use the Sales Report dashboard:

1. **Explore Sections**: Navigate the 2x2 grid to view each visualization.
2. **Interact with Data**: Hover over bars, pie segments, or map markers to reveal detailed figures.
3. **Customize Views**: Utilize filters or dropdowns (if available) to focus on specific data subsets.
4. **Analyze Insights**: Interpret trends, patterns, or outliers to inform business decisions.

## Contact Information

For questions, support, or additional details, please contact [insert contact information here].
