# Day 4 — Correlation & Parameterization

## What We Created
- Added dynamic authentication token correlation.
- Added dynamic Booking ID correlation.
- Added Update Booking and Get Updated Booking requests.
- Added CSV-based test data parameterization.
- Created `booking-api-correlation-parameterization.jmx`.

## Input / Configuration
- Auth token extracted using JSON Extractor.
- Booking ID extracted from Create Booking response.
- CSV variables:
  `firstname, lastname, totalprice, depositpaid, checkin, checkout, additionalneeds`
- CSV data contains 5 booking records.
- Dynamic values used with `${variable}`.

## Output / Results
- Authentication token correlation: PASS
- Booking ID correlation: PASS
- Update Booking: PASS
- Get Updated Booking: PASS
- CSV parameterization: PASS
- 1 user × 3 loops successfully used different CSV records.

## Issue Faced / Fix
- CSV file was initially configured as `.csv.xlsx`.
- File encoding/CSV configuration was incorrect.
- Fixed by using a proper `.csv` file and correct CSV Data Set Config settings.

## Key Learning
- **Correlation:** Capture dynamic data from one response and reuse it in later requests.
- **Parameterization:** Supply different test data from an external CSV file.
- JMeter variables can be reused using `${variable}`.