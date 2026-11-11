# AI Log & Cleaning Court Reflection

## Cleaning Code Court Verdicts

| Line / Code Block Tested | Action Proposed | Verdict (Keep / Modify / Reject) | Evidence & Reasoning |
| :--- | :--- | :--- | :--- |
| `df.drop_duplicates()` | Remove identical row duplicates | **Keep** | Before/after row counts confirmed duplicate transaction logs were removed without dropping distinct valid entries. |
| `df['price'].fillna(0)` | Fill missing prices with 0 | **Reject** | Imputing 0 distorts summary statistics (`mean`, `median`) and treats unrecorded prices as free items. |
| `df['item'].str.strip().str.title()` | Clean whitespace and case | **Keep** | Standardized item labels so that categories like `'milk'` and `'Milk '` group together correctly. |
| `df[df['price'] < 0]` | Drop negative price rows | **Modify** | Retained and flagged negative entries for audit instead of silently deleting, preserving potential return/refund records. |

## Reflection & Verification

- **Differences from AI Recommendations:** The AI suggested aggressively dropping all missing values and auto-filling zero for unrecorded prices. I rejected zero-imputation to preserve audit integrity.
- **What I Would Have Missed Alone:** The AI code highlighted subtle leading/trailing spaces in text columns that were not immediately visible during manual inspection.
- **Final Item Counts:** Verified that post-cleaning item frequencies match expected distribution without unrecorded silent data loss.
