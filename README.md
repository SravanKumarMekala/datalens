# DataLens — SQL & Python Analytics Dashboard 📊

A data analytics dashboard that visualizes sales data using SQL query patterns, Python data pipeline concepts, and interactive JavaScript charts. Demonstrates the full data engineering workflow from raw SQL to visual insights.

🔗 **Live Demo:** [https://yourusername.github.io/datalens](https://yourusername.github.io/datalens)

---

## 📸 Preview

> A GitHub-inspired dark dashboard featuring a live SQL query panel, KPI cards, multi-chart visualizations, and a sortable data table.

---

## ✨ Features

- 🗄️ **SQL Query Panel** — Displays a real-world aggregation query with syntax highlighting (SELECT, JOIN, GROUP BY, HAVING, Window Functions)
- ▶️ **Simulate Query Run** — Animated "running" state that mimics real DB execution time
- 📦 **KPI Cards** — Total Revenue, Orders, Average Order Value, Churn Rate
- 📈 **Line Chart** — Monthly revenue trend by category (FY 2024)
- 🥧 **Doughnut Chart** — Revenue distribution across product categories
- 📊 **Bar Chart** — Top 5 products by average order value
- 📋 **Data Table** — Query result table with growth % and status badges
- 🏷️ **Tech badges** — Python / SQL / JavaScript clearly labeled
- 📱 **Fully responsive** — Adapts from mobile to widescreen

---

## 🛠️ Tech Stack

| Technology | Usage |
|---|---|
| HTML5 | Structure and layout |
| CSS3 | Dark theme, CSS variables, responsive grid |
| JavaScript (ES6+) | Chart rendering, UI interactions |
| Chart.js v4 | Line, Doughnut, and Bar charts |
| Google Fonts | Typography (IBM Plex Mono + IBM Plex Sans) |
| SQL | Query logic displayed in the panel |
| Python (concept) | Data pipeline: SQLite → pandas → REST API |

---

## 📂 Project Structure

```
datalens/
└── index.html        # Single-file app (HTML + CSS + JS + Chart.js CDN)
```

---

## 🚀 How to Run Locally

```bash
# No installation needed!
Double-click index.html  # Opens directly in your browser
# Requires internet connection (Chart.js loaded from CDN)
```

---

## 🧠 Concepts Demonstrated

### SQL Concepts
- **Window Functions** — `LAG()` with `PARTITION BY` for YoY growth calculation
- **Aggregate Functions** — `SUM()`, `COUNT()`, `AVG()`, `ROUND()`
- **JOINs** — `INNER JOIN` between sales and products tables
- **Filtering** — `WHERE` with date range, `GROUP BY` with `ORDER BY`
- **Aliases** — Clean column naming with `AS`

### Python Data Pipeline (Conceptual)
```
SQLite Database
      ↓
Python (pandas) — data cleaning, aggregation
      ↓
REST API (Flask/FastAPI) — JSON endpoint
      ↓
JavaScript (Chart.js) — data visualization
```

### JavaScript / Frontend
- **Chart.js Integration** — Initializing Line, Doughnut, and Bar charts
- **Chart Configuration** — Custom colors, fonts, grid styles, tooltips
- **DOM Manipulation** — Dynamic button state updates
- **CSS Grid** — Responsive 2-column chart layout
- **CSS Custom Properties** — Consistent color theming

### Data Analysis Concepts
- **KPI Tracking** — Revenue, orders, AOV, churn
- **Time Series Analysis** — Monthly trend line charts
- **Category Breakdown** — Pie/doughnut distribution charts
- **Comparative Analysis** — Bar charts for ranking
- **Growth Rate Calculation** — `(current - previous) / previous * 100`

---

## 📊 Sample SQL Query Explained

```sql
SELECT
    s.category,
    SUM(s.revenue) AS total_revenue,          -- Total sales per category
    COUNT(s.order_id) AS total_orders,         -- Number of orders
    AVG(s.revenue) AS avg_order_value,         -- Average deal size
    ROUND(
        (SUM(s.revenue) - LAG(SUM(s.revenue)) -- Window function: previous month
        OVER (PARTITION BY s.category ORDER BY s.month))
        / LAG(SUM(s.revenue)) OVER (...)
        * 100, 2
    ) AS growth_pct                            -- Month-over-month growth %
FROM sales s
JOIN products p ON s.product_id = p.id
WHERE s.month BETWEEN '2024-01' AND '2024-12'
GROUP BY s.category, s.month
ORDER BY total_revenue DESC;
```

---

## 🌱 Future Enhancements

- [ ] Connect to a real SQLite database via Python Flask backend
- [ ] Add date range picker to filter chart data dynamically
- [ ] Export data table to CSV
- [ ] Add regression/forecasting line on the trend chart
- [ ] Deploy backend to Railway or Render

---

## 👨‍💻 Author

**Sravan Kumar Mekala**
- 📧 mekalasravankumar66@gmail.com
- 🔗 [LinkedIn](https://www.linkedin.com/in/sravankumar-mekala-963096336)
- 🐙 [GitHub](https://github.com/yourusername)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
