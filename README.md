# Zorvyn Finance Dashboard

A premium, Bloomberg-inspired finance dashboard built with React + Vite. Submitted for the **Frontend Developer Intern** screening assessment.

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ and npm

### Setup

```bash
# 1. Install dependencies
npm install

# 2. Start development server
npm run dev

# 3. Open in browser
# → http://localhost:5173
```

### Build for production
```bash
npm run build
npm run preview
```

---

## 📁 Project Structure

```
src/
├── components/
│   ├── charts/
│   │   ├── BalanceTrendChart.jsx   # Area chart — 6-month balance + income trend
│   │   └── SpendingDonut.jsx       # Donut chart — spending by category
│   ├── insights/
│   │   └── InsightsPage.jsx        # Monthly bar chart, top category, savings rate
│   ├── layout/
│   │   ├── DashboardPage.jsx       # Overview page — summary cards + recent activity
│   │   ├── SummaryCards.jsx        # Balance / Income / Expense stat cards
│   │   ├── Sidebar.jsx             # Navigation sidebar
│   │   ├── Topbar.jsx              # Header — role switcher + theme toggle
│   │   └── TickerStrip.jsx         # Scrolling market ticker (mock data)
│   └── transactions/
│       ├── TransactionsPage.jsx    # Full transactions table with filters + pagination
│       └── TxnModal.jsx            # Add / Edit transaction modal
├── context/
│   └── AppContext.jsx              # Global state via useReducer + LocalStorage sync
├── data/
│   └── transactions.js             # 71 mock transactions (Jan–Jun 2025) + helpers
├── utils/
│   └── index.js                    # formatINR, formatDate, filtering, CSV export
├── App.jsx
├── main.jsx
└── index.css                       # All styles — CSS variables, dark/light theme
```

---

## ✨ Features

### Dashboard Overview
- **Summary Cards** — Net Balance, Total Income, Total Expenses with savings rate
- **Balance Trend Chart** — 6-month area chart (balance + income overlay)
- **Spending Donut Chart** — top 7 categories with percentage labels
- **Recent Activity** — last 8 transactions inline

### Transactions
- **71 realistic mock transactions** across Jan–Jun 2025
- **Search** by description or category
- **Filter** by type (income/expense), category, and date range
- **Sort** by date, amount, or category (ascending/descending)
- **Pagination** — 12 per page with smart ellipsis
- **CSV Export** — exports current filtered view
- **Admin-only**: Add, Edit, Delete transactions

### Insights
- Highest spending category with recommendation
- Savings rate with qualitative assessment (good / low / excellent)
- Best performing month by net surplus
- Month-over-month expense change (%)
- Monthly income vs expense bar chart
- Full category spending breakdown with proportional progress bars

### Role-Based UI
| Feature              | Viewer | Admin |
|----------------------|--------|-------|
| View all data        | ✅     | ✅    |
| Add transactions     | ❌     | ✅    |
| Edit transactions    | ❌     | ✅    |
| Delete transactions  | ❌     | ✅    |
| Export CSV           | ✅     | ✅    |

Switch roles instantly via the **Viewer / Admin** toggle in the top bar.

### Optional Enhancements Implemented
- ✅ **Dark / Light mode** — toggle in top bar, persisted to localStorage
- ✅ **LocalStorage persistence** — transactions, role, and theme survive page refresh
- ✅ **CSV Export** — exports filtered transaction set with one click

---

## 🎨 Design Decisions

**Aesthetic**: Bloomberg terminal-inspired dark theme — near-black backgrounds (#0a0b0d), muted dark surfaces, gold (#E8B84B) as the primary accent, green/red for income/expense. Light mode is a full counterpart, not an afterthought.

**Typography**:
- Display / headings: `Syne` (geometric, editorial)
- Body: `DM Sans` (clean, readable)
- Numbers / data: `DM Mono` (monospaced for alignment)

**Layout**: Sticky sidebar + fixed topbar shell. Responsive — sidebar collapses to a bottom tab bar on mobile.

**State Management**: React `useReducer` via Context API. All state lives in one reducer (`AppContext`), making data flow predictable. Side effects (localStorage sync, theme class) handled in `useEffect`.

**Data**: 71 hand-crafted transactions across 6 months for realistic chart curves and meaningful insights.

---

## 🛠 Tech Stack

| Tool         | Version  | Purpose                        |
|--------------|----------|--------------------------------|
| React        | 18.2     | UI framework                   |
| Vite         | 5.2      | Build tool & dev server        |
| Recharts     | 2.10     | AreaChart, BarChart, PieChart  |
| Lucide React | 0.383    | Icons                          |
| date-fns     | 3.6      | Date formatting                |

No UI component library — all styles are hand-written CSS with custom properties.

---

## 📝 Assumptions

- All monetary values are in **Indian Rupees (₹)**
- "Balance" is cumulative from a ₹1,20,000 opening balance
- Role switching is frontend-only simulation (no auth / backend)
- Mock data covers Jan 2025 – Jun 2025

---

*Built by Mo Gilman Khan · Zorvyn Frontend Intern Assessment · April 2026*
