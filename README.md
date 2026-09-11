# sqlite-articles-management
# Articles Portal (Portal Articole) - Database & Analytics Web Application

A full-stack SQLite database management system and interactive web application built with **Python**, **Streamlit**, and **SQLite3**. The platform provides relational database administration (CRUD operations), business analytics, key performance indicators (KPIs), and interactive data visualizations for managing a publishing or content management portal.

---

## 🌟 Key Features

### 1. Database Administration & Back-End (CRUD)
- **Complete Relational Operations**: Full support for `CREATE`, `READ`, `UPDATE`, and `DELETE` operations across all core entities (`Articles`, `Authors`, `Categories`, `Comments`).
- **Foreign Key Constraints & Cascade Operations**: Enforces data integrity (e.g., automatically handling dependent records or cascade deletes).
- **Interactive Management UI**: Direct control over publishing statuses (`publicat`, `draft`, `arhivat`), views, author data, and article ratings.

### 2. Analytical Front-End (10 Specialized Objectives)
The application translates database queries into clear tabular views, dynamic charts, and actionable editorial insights:
1. **O1 — Published Articles Overview**: Queries articles with author names, categories, view counts, and status ordered by engagement.
2. **O2 — Category Distribution**: Categorical breakdown showing covered vs. unassigned editorial areas.
3. **O3 — Author Engagement Metrics**: Aggregates total publications and total view counts per author.
4. **O4 — Average Category Ratings**: Analyzes reader satisfaction scores across content categories.
5. **O5 — Uncommented Content Detection**: Identifies published articles lacking audience interaction.
6. **O6 — Top 5 Articles by Reach**: Highlights high-performing content to guide future topic strategy.
7. **O7 — Publication Rate Analysis**: Calculates the ratio of published vs. draft/archived articles.
8. **O8 — Underperforming Content Alert**: Detects articles below critical threshold (<50 views) for targeted promotion.
9. **O9 — Core Averages**: Calculates average views and average comments per published article.
10. **O10 — Complete Portal Dashboard**: Comprehensive view synthesizing reach, audience engagement, and perceived quality across all records.

### 3. Integrated Live View & Performance Scorecard (KPI / IPE)
- **Live Impact Feedback**: Real-time synchronization where CRUD updates instantly update analytic charts and metrics.
- **Editorial Performance Indicator (IPE)**: An automated composite KPI score (0–100) evaluating 5 core benchmarks:
  - Publication Rate $\ge 80\%$
  - Average Views per Article $\ge 100$
  - Average Rating $\ge 4.0$
  - Uncommented Articles $\le 25\%$
  - Underperforming Articles $\le 2$
- **Automated Strategic Recommendations**: Dynamically generates tailored editorial actions based on current database thresholds and KPI status.

---

## 🗄️ Database Architecture

The system operates on an **SQLite** database (`LAB1.db`) with four primary tables:

```
+--------------------+       +--------------------+
|      Autori        |       |     Categorii      |
+--------------------+       +--------------------+
| id_autor (PK)      |       | id_categorie (PK)  |
| nume               |       | nume_categorie     |
| prenume            |       | descriere          |
| email              |       +---------+----------+
| data_inregistrare  |                 |
+---------+----------+                 |
          | 1                          | 1
          |                            |
          | N                          | N
+---------+----------------------------+----------+
|                      Articole                   |
+-------------------------------------------------+
| id_articol (PK)                                 |
| titlu                                           |
| continut                                        |
| data_publicarii                                 |
| id_autor (FK -> Autori.id_autor)                |
| id_categorie (FK -> Categorii.id_categorie)     |
| numar_vizualizari                               |
| status ('publicat', 'draft', 'arhivat')         |
+------------------------+------------------------+
                         | 1
                         |
                         | N
                +--------+-----------+
                |    Comentarii      |
                +--------------------+
                | id_comentariu (PK) |
                | id_articol (FK)    |
                | autor_comentariu   |
                | text_comentariu    |
                | data_comentariu    |
                | evaluare (1-5)     |
                +--------------------+
```

---

## 📁 Project Structure

```
.
├── ST_VR_1/                    # Basic SQL Trainer & CRUD variant
│   ├── sql_crud_trainer.py     # Streamlit interface for SQL execution & CRUD
│   └── LAB1.db                 # SQLite Database file
├── ST_VR_2/                    # Advanced Dashboard & KPI Portal variant
│   ├── sql_crud_trainer.py     # Feature-rich Streamlit application (CRUD + 10 Objectives + KPI)
│   └── LAB1.db                 # SQLite Database file
└── README.md                   # Project Documentation
```

---

## 🛠️ Technology Stack

- **Language**: Python 3.9+
- **Database**: SQLite3
- **Web Framework**: Streamlit
- **Data Visualization**: Native Streamlit Markdown & Charting utilities

---

## 🚀 Getting Started

### Prerequisites
Ensure Python 3.8+ is installed on your system.

### Installation

1. **Clone the Repository or Extract the Project Files**:
   ```bash
   git clone <repository-url>
   cd <project-folder>
   ```

2. **Install Required Packages**:
   ```bash
   pip install streamlit
   ```

### Running the Application

You can launch either variant of the project using Streamlit:

#### Advanced Portal with Analytics & KPI Scorecard (Recommended):
```bash
streamlit run ST_VR_2/sql_crud_trainer.py
```

#### SQL Trainer & Basic CRUD Interface:
```bash
streamlit run ST_VR_1/sql_crud_trainer.py
```

---

## 📊 Usage Guide

1. **Back-End (CRUD)**:
   - Select a table (`Articole`, `Autori`, `Categorii`, `Comentarii`).
   - Perform `READ`, `CREATE`, `UPDATE`, or `DELETE` queries with built-in forms.
2. **Front-End (10 Objectives)**:
   - Expand any objective to view the raw SQL statement executed, tabular results, corresponding bar charts, and editorial analysis.
3. **Combined View + KPI**:
   - Make quick updates to article metrics (e.g., status, view counts).
   - Watch the live dashboard, IPE Scorecard, and automated editorial recommendations adjust dynamically.
