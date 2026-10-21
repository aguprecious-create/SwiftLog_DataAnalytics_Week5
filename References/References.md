# References and method notes

## Source data

All data comes from the SwiftLog project files supplied with the Week 5 brief (`Week_5_files.zip`). The files are listed in `Data/Original Datasets/`. The data is synthetic and created for training purposes.

## Definitions and calculations

- **Net revenue:** sum of quantity multiplied by unit price for order items whose order status is not Cancelled.
- **Gross revenue:** the same calculation across all orders.
- **Average order value:** net revenue divided by the number of non-cancelled orders.
- **On-time delivery rate:** shipments with Status = "On Time" in Delivery_Performance, divided by all shipments.
- **Delayed rate (Status):** shipments with Status = "Delayed", divided by all shipments.
- **Delayed rate (delay days):** shipments with DelayDays above zero, divided by all shipments. Not used on the dashboard cards.
- **On-time within X days:** shipments with DelayDays at or below the threshold, divided by all shipments. The threshold is set with the What-If parameter.
- **Return rate:** distinct orders with at least one return record, divided by all orders.
- **Product return rate:** distinct returned orders for a product, divided by distinct orders containing that product.
- **Customer retention rate:** customers with more than one order, divided by all customers.
- **Units sold to stock ratio:** total units sold divided by total stock held. This is a unit-based proxy, because the data has no cost figures.
- **Warehouse Stock Share:** each location's stock as a share of total stock. A proxy for utilisation, because no capacity data is available.

## Methods

- Data quality checks: missing values, duplicate keys and foreign-key relationships were tested for every table. No orphaned records were found.
- Inventory was aggregated by warehouse and product, with stock summed across duplicate rows.
- SQL analysis was run in DuckDB. The Python analysis was run in Jupyter.
- Key figures were checked across Excel, SQL, Python and Power BI.

## Tools

Microsoft Excel, DuckDB, Python (pandas, matplotlib, seaborn), Power BI Desktop, Microsoft PowerPoint.
