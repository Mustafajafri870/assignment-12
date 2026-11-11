# My Pre-AI Audit & Decisions (Before AI)

## Step 1: Pre-AI Diagnosis & Audit Log
| Problem Identified | Code That Revealed It | Planned Decision | Reason / Justification |
| :--- | :--- | :--- | :--- |
| Missing price/item entries | `df.isnull().sum()` / `df.info()` | Retain / Flag | Need to audit whether missing values are structural or corrupt data before dropping. |
| Duplicate ledger rows | `df.duplicated().sum()` | Exclude (Drop) | Identical duplicate transaction entries distort true ledger counts. |
| Inconsistent text casing / whitespace | `df['item'].value_counts()` | Correct | Whitespace and mixed uppercase/lowercase create redundant category buckets. |
| Negative or zero price values | `df.describe()` | Flag | Negative prices indicate potential return transactions or data entry errors. |
| Non-standard date formats | `df.head()` / `df.dtypes` | Correct | Standardizing date formatting ensures accurate chronological filtering. |

## Step 2: Diagnostic Code Plan
- `df.shape`: Check total rows and columns.
- `df.info()` & `df.describe()`: Summary of data types, missing counts, and numerical distributions.
- `df['item'].unique()`: Verify distinct item counts before and after text cleaning.
