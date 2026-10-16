# Value Index Construction & Rebalancing

## Overview

This project builds and tests a reusable Python class to construct and rebalance a value index of 50 stocks, using value scores, buffer rules, and constrained weight optimisation.

## Methodology

**1. Data Processing**
- Load stock data from Excel for each rebalance date.
- Convert data types and validate data quality.

**2. Index Construction**
- Select the top 40 stocks by value score.
- Apply the buffer rule to existing stocks ranked 41–60.
- Fill the remaining positions to reach 50 stocks.

**3. Weight Optimisation**
- Calculate initial weights using free-float market capitalisation weights and value scores.
- Use SLSQP to minimise deviations from initial weights.
- Apply four constraints:
  - Maximum stock weight: min(5%, 20 × FCap Wt)
  - Minimum stock weight: 0.05%
  - Maximum sector weight: 50%
  - Total weight: 100%

**4. Rebalancing & Output**
- Run three consecutive rebalances.
- Update previous constituents for the next rebalance.
- Export results to Excel.

## Testing

- **General Checks:** Stock count, unique identifiers, and invalid dates.
- **Index Rules Checks:** Weight constraints and buffer rule validation.
- **Output Check:** 150 rows across three rebalances.

## Technologies

- Python
- Pandas
- NumPy
- SciPy (SLSQP)
- Excel

## Future Improvements

- Make fixed parameters configurable.
- Add more edge-case and stability tests.
- Support persistent storage of previous constituents.

## AI Assistance

ChatGPT and Claude were used to assist with code development and review. The implementation was reviewed and tested.
