# 🚗 Car Rental Management System
> A complete car rental management application with modern GUI built using Python, CustomTkinter, and MySQL. Developed as a mini project for Computer Science at iTeam University.

---

## 📖 About The Project

This system helps car rental agencies automate and optimize their daily operations: vehicle fleet management, customer registration, rental processing, automatic document generation, and real-time statistics tracking.

# 🚀 Quick Installation

## Prerequisites
- Python 3.12+
- MySQL 8.0+ or XAMPP

---

## Setup (5 minutes)

### 1. Clone & Install
```bash
git clone https://github.com/onsdev2001/car-rental-system.git
cd car-rental-system
pip install -r requirements.txt
```

### 2. Start MySQL
**XAMPP:** Open Control Panel → Start MySQL (green)  
**MySQL:** Ensure service is running

### 3. Create Database
```sql
CREATE DATABASE location_voitures CHARACTER SET utf8mb4;
USE location_voitures;
SOURCE database/schema.sql;
```

Or use **phpMyAdmin:** http://localhost/phpmyadmin
- New database: `location_voitures`
- Import: `database/schema.sql`

### 4. Configure
Edit `config.py`:
```python
DB_HOST = "localhost"
DB_USER = "root"
DB_PASSWORD = ""  
DB_NAME = "location_voitures"
```

### 5. Run
```bash
python main.py
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| MySQL connection failed | Check XAMPP running + credentials in `config.py` |
| Module not found | `pip install -r requirements.txt --upgrade` |
| Port 3306 in use | Change to 3307 in XAMPP config |

---

## Database Schema

```sql
Voiture (num_imma PK, marque, modele, kilometrage, etat, prix_location)
Locataire (id_loc PK, nom, prenom, adresse)
Location (id_location PK, num_imma FK, id_loc FK, date_location, date_retour)
```

Full schema: `database/schema.sql`

---

## First Run

1. Add vehicle: **Voitures** tab → Fill form → Add
2. Add customer: **Locataires** tab → Fill form → Add
3. Rent car: **Locations** → Available → Rent → Enter customer ID
4. View stats: **Statistiques** tab

---

**Done!** 🎉
---

## ✨ Key Features

### 🚗 Vehicle Management
- Add, edit, delete vehicles
- Automatic maintenance alerts (>100,000 km)
- Professional Excel export

### 👥 Customer Management
- Customer registration with auto-generated ID
- Smart unified search (ID or name)
- Alphabetically sorted list
- Full CRUD operations

### 📋 Rental Operations
- **Rent a car** - Automatic validation + PDF contract generation
- **Return a car** - Auto-calculation of duration and cost
- 4 tabs: Available, Rented, Active, History
- Transaction security with rollback

### 📊 Statistics Dashboard
- 6 colorful stat cards (total, available, rented, occupancy rate, revenue, customers)
- 3 interactive charts (availability, top 5 cars, brand distribution)
- Maintenance alerts section
- Real-time auto-refresh

### 📄 Documents & Exports
- Professional Excel exports (formatted headers, auto-adjusted columns)
- Automatic PDF contract generation (logo, sections, terms)
- Timestamped file names

---

## 🛠️ Technologies

| Category | Technology |
|----------|-----------|
| **Language** | Python 3.12+ |
| **GUI** | CustomTkinter 5.2+ |
| **Database** | MySQL 8.0 |
| **Architecture** | MVC Pattern |
| **PDF** | reportlab 4.0+ |
| **Excel** | openpyxl 3.1+ |
| **Charts** | matplotlib 3.8+ |

---

## 🚀 Quick Start

### Prerequisites

- ✅ **Python 3.12+** ([Download](https://www.python.org/downloads/))
- ✅ **MySQL 8.0+** or **XAMPP** ([Download](https://www.apachefriends.org/))


** Run application**
```
python main.py
```


---

## 📱 How To Use

### 🚗 Rent a Car (Step-by-Step)

1. **Go to Rentals tab** → "Available Vehicles"
2. **Find your car** in the list
3. **Click "🚗 Rent"** button
4. **Enter Customer ID** in the popup (e.g., `5`)
5. **Click Confirm**

**What happens:**
- ✅ System validates availability
- ✅ Checks customer exists
- ✅ Creates rental in database
- ✅ Generates PDF contract automatically
- ✅ Shows success message
- 📄 **Option to open PDF contract**

**Example:**
```
Car: 123 TUN 1234 - Renault Clio
Customer ID: 5 (JEBALI Karim)
Date: 22/01/2026
→ Contract generated: contrat_5_20260122.pdf
```

---

### ↩️ Return a Car

1. **Go to "Rented Vehicles"** tab
2. **Find the rented car**
3. **Click "↩️ Return"**
4. **Confirm**

**What happens:**
- ✅ Calculates rental duration (days)
- ✅ Calculates total cost (duration × daily rate)
- ✅ Updates database
- ✅ Car becomes available again

**Example:**
```
Car: Renault Clio
Rented: 20/01/2026
Returned: 23/01/2026
→ Duration: 3 days
→ Cost: 3 × 80 DT = 240 DT
```

---

### 👥 Add a Customer

1. **Go to Customers tab**
2. **Fill the form:**
   - Last Name: `BEN AHMED`
   - First Name: `Mohamed`
   - Address: `15 Avenue Bourguiba, Tunis`
3. **Click "➕ Add"**
4. **ID generated automatically** (e.g., ID: 11)

---

### 🔍 Search a Customer

**By ID:**
```
Type: 5
→ Finds customer with ID 5 instantly
```

**By Name:**
```
Type: ben
→ Finds "BEN AHMED Mohamed"
(Case-insensitive, partial match)
```

---

### 📊 View Statistics

1. **Go to Statistics tab**
2. **See real-time dashboard:**
   - 📦 Total Vehicles: 12
   - 🟢 Available: 8
   - 🔴 Rented: 3
   - 📈 Occupancy: 25%
   - 💰 Revenue: 1,110 DT/day
   - 👥 Customers: 10

3. **View charts:**
   - Bar chart: Availability
   - Top 5 most rented cars
   - Brand distribution pie chart

4. **Check alerts:**
   - ⚠️ Vehicles > 100,000 km
   - Maintenance recommendations

---

### 📄 Export to Excel

**From any module:**
1. **Click "📊 Export to Excel"**
2. **File generated** with timestamp
3. **Choose to open** or save

**Example filename:**
```
exports/voitures_20260122_143025.xlsx
```

**Features:**
- Professional formatting
- Color-coded headers
- Auto-adjusted columns
- Borders and styling

---

## 📂 Project Structure

car-rental-system/
│
├── main.py              # Entry point
├── config.py            # Database settings
├── controller.py        # Business logic (MVC)
├── database.py          # MySQL connection
├── models.py            # Data models
├── views.py             # GUI interface
├── export_utils.py      # PDF/Excel generation
├── requirements.txt     # Dependencies
│
├── database/
│   └── schema.sql       # Database creation script
│
├── exports/             # Generated files
│   ├── *.xlsx           # Excel exports
│   └── contrats/        # PDF contracts
│
└── docs/                # Documentation
    ├── rapport.pdf      # Project report
    └── presentation.pptx # PowerPoint slides

---


## 🔐 Security

✅ **Parameterized SQL queries** (prevents injection)  
✅ **Multi-level validation** (UI + Logic + Database)  
✅ **ACID transactions** (rollback on error)  
✅ **Foreign key constraints** (data integrity)

---


## 📄 License

Educational project - iTeam University

---

## 👤 Author

**Student TC-ING-2**  
iTeam University - Computer Science  
📧 khdimaallahons@gmail.com 
🔗 [Ons Khdimaallah](https://github.com/onsdev2001)

**Year:** 2025-2026

---

## 🙏 Acknowledgments

- iTeam University - Computer Science Department
- Python & CustomTkinter communities
- All contributors and testers

---

**Made with ❤️ using Python**
