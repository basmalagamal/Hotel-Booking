# Hotel-Booking
# 🏨 Hotel Booking Cancellation Prediction

This project analyzes hotel booking data to predict whether a reservation will be **canceled** or **not canceled**.  
It involves **data cleaning, preprocessing, feature engineering, and machine learning modeling**.

---

## 📂 Dataset

- **Source**: Hotel Booking Dataset  
- **Shape**: ~119k rows × 32 columns  
- **Target Variable**: `is_canceled` (0 = Not Canceled, 1 = Canceled)

### Key Columns:
- `hotel`: Type of hotel (Resort or City).
- `lead_time`: Number of days before arrival when booking was made.
- `arrival_date_year`, `arrival_date_month`, etc.
- `stays_in_weekend_nights`, `stays_in_week_nights`: Nights stayed.
- `adults`, `children`, `babies`: Guests composition.
- `meal`, `market_segment`, `country`: Categorical features.
- `adr`: Average Daily Rate.
- `is_canceled`: **Target column**.

---

## 🛠️ Project Workflow

### 1. **Data Cleaning**
- Removed duplicates.
- Dropped irrelevant columns (`company`, `agent`).
- Handled missing values:
  - Dropped rows with missing `country` or `children`.
- Removed extreme outliers (e.g., `adr > 1000`).

### 2. **Exploratory Data Analysis (EDA)**
- Visualized distributions of numerical features (histograms & boxplots).
- Checked class balance for `is_canceled`.
- Detected outliers in `adr`, `lead_time`, `adults`.

### 3. **Feature Engineering**
- Created new features:
  - `total_guests = adults + children + babies`
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
  - `is_family = 1 if (children + babies > 0) else 0`
- Encoded categorical variables:
  - **One-Hot Encoding** for low-cardinality columns (`meal`, `market_segment`, etc.).
  - **Frequency Encoding** for high-cardinality column (`country`).
  - Also tried **Label Encoding** version.

### 4. **Preprocessing**
- Scaled numerical features using **StandardScaler**.
- Encoded categorical variables.

### 5. **Data Splitting**
- Train-test split: 80% training, 20% testing.
