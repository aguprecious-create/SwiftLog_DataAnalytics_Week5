# SwiftLog Logistics: Data Analytics Submission (Week 5)

This folder holds the Data Analytics track submission for the SwiftLog Logistics Analytics project. It covers data preparation, the Power BI dashboard, business analysis, recommendations and the executive report and presentation.

## Folder contents

| Folder | Contents |
|---|---|
| `Data/Original Datasets/` | The eleven SwiftLog CSV tables and the data dictionary, unchanged from the project files. |
| `Dashboard/` | `SwiftLog_Analytics.pbix`, the Power BI report with five analysis pages, a Customer Detail drill-through page and a Warehouse Tooltip page. |
| `Report/` | `Executive_BI_Report.pdf` (three-page executive report) and `Dashboard_Screenshots.pdf` (one capture per dashboard page). |
| `Presentation/` | `Executive_Presentation.pptx` (fifteen slides). |
| `Images/` | Background images used for the dashboard layout. |
| `References/` | Sources, definitions and method notes. |

## Tools

- Microsoft Excel: data quality assessment and cleaning workbook
- DuckDB / SQL: business queries (see the Part 2 transformation log and the SQL analysis)
- Python (pandas, matplotlib, seaborn): exploratory analysis
- Power BI Desktop: data model, DAX measures, dashboard

## Opening the dashboard

1. Open `Dashboard/SwiftLog_Analytics.pbix` in Power BI Desktop.
2. If prompted, refresh the data. The model reads the cleaned source tables.
3. Use the Status, City, Location and Delay Threshold filters on each page. Bookmarks at the top of the Executive Overview switch between All Orders, Delivered and Pending.
4. Right-click a customer on the Customer Analytics page and choose Drill through to open Customer Detail.

## Data model

Ten one-to-many relationships connect the dimension tables (Customers, Products, Warehouses, Employees) to the fact tables (Orders, Order_Items, Shipments, Delivery_Performance, Inventory, Returns). Suppliers is not connected, because it has no key that links it to any other table. Inventory was aggregated from 4,000 rows to 2,455 by warehouse and product.

## Key definitions

- **Net revenue:** revenue from non-cancelled orders. This is the headline revenue figure.
- **Revenue:** quantity multiplied by the product's current unit price, since the data has no price history.
- **On-time and delayed rates:** based on the Status field in Delivery_Performance.
- **Return rate:** orders with at least one return, divided by all orders.
- **Customer retention:** customers with more than one order, divided by all customers.

## Known limitations

- The delivery Status field and the DelayDays field disagree for 1,203 shipments. The on-time rate uses Status.
- 1,626 shipments belong to cancelled orders and 1,716 to pending orders.
- Supplier performance cannot be measured because suppliers have no link to products or shipments.
- Warehouse capacity and delivery dates are not in the data. Warehouse Stock Share and Average Delivery Delay are used as proxies.
- The data covers January to September 2026. September is a partial month.

The source data is synthetic and created for training purposes.
