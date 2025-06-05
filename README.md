# Data Cleaning Framework README

**GameZone Dataset**  
**Owner:** Christine Jiang  
**Data Type:** Excel File  

---

## 📄 Description
Clean raw data in an Excel file by cleaning nonsensical values, missing values, etc., using a five-step framework called **CLEAN**:

- **C**: Conceptualize the data  
- **L**: Locate solvable values  
- **E**: Evaluate unsolvable values  
- **A**: Augment the data  
- **N**: Note and document  

---

## 🧠 Data Cleaning Philosophy
Few, if any, datasets are perfect. The goal is to clean data so that it’s sufficient to analyze, share, and iterate on.

---

## 🔧 Data Cleaning Steps

### Step 1: Remove Obvious “Dirty” Values
- Polish and standardize the remaining values.
- Refine and revisit the data after initial analysis.

---

## 🏢 Company Context
**Company:** *GameZone* (fictitious company)  
**Founded:** 2018  
**Business:** Sells new & refurbished gaming products.  
**Sales Channels:** Primarily online, with additional sales via a mobile app and various marketing channels.  
**Dataset Size:** 20k records (modeled after a realistic business dataset).  

---

## 📊 Dataset Structure

### 📋 Columns (on **Orders** tab unless otherwise noted)
- `User_ID`
- `Order_ID`
- `Purchase_TS`
- `Ship_TS`
- `Product_Name`
- `Product_ID`
- `USD_Price`
- `Purchase_Platform`
- `Marketing_Channel`
- `Account_Creation_Method`
- `Country_Code`
- `Country_Code` *(on Region tab)*
- `Region` *(on Region tab)*

### 🗂 Tabs:
- Orders  
- Region

---

## 🧩 Conceptualize the Data

### Preparation Questions:
- What type of data am I reviewing?
- What business questions are being asked?

**Key Business Question:**  
> “What are the overall sales trends across a variety of regions?”

### Data Field Overview:
| Field | Description |
|-------|-------------|
| `User_ID` | Each row is assigned to a unique user |
| `Order_ID` | Identifier for each order |
| `Purchase_TS` | Date of the order |
| `Ship_TS` | Date the order was shipped |
| `Product_Name` | Name of the product shipped |
| `Product_ID` | Product code |
| `USD_Price` | Price paid by the customer |
| `Purchase_Platform` | Platform used to purchase |
| `Marketing_Channel` | How the customer discovered the site |
| `Account_Creation_Method` | How the account was created |
| `Country_Code` | Customer’s location |

### Key Metrics:
- `USD_Price`

### Key Dimensions:
- Time of Purchase (`Purchase_TS`)
- Date of Shipment (`Ship_TS`)
- Product Name
- Purchase Platform
- Marketing Channel
- Account Creation Method
- Country Code

---

## 🛠️ Locate Solvable Values
- Inconsistent formats/categorizations
- Null values
- Duplicate values

### Actions:
- Add a tab called **Issues Log**
- Filter to find distinct values
- Duplicate Orders and Region tabs to preserve originals
- Create duplicate columns for cleaned fields
- Document each issue in **Issues Log**

---

## 🚫 Evaluate Unsolvable Issues
### Typical Causes:
- Missing dates
- Outliers
- Business logic violations (e.g., `Ship_TS` before `Purchase_TS`)

> If the issue magnitude is **< 20%**, document it.  
> If it's **> 20%**, resolve or escalate.

**Validation Rule Example:**  
```excel
=E2 >= F2
