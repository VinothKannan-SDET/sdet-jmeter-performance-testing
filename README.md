![JMeter Performance Test](https://github.com/VinothKannan-SDET/sdet-jmeter-performance-testing/actions/workflows/jmeter-performance.yml/badge.svg)

## Repository
[GitHub Repository](https://github.com/VinothKannan-SDET/sdet-jmeter-performance-testing)

# JMeter Performance Testing — Restful Booker API

## Overview
Performance test suite built with Apache JMeter against the
Restful Booker API, covering baseline, load, stress testing
with correlation, parameterization, assertions and HTML reporting.

## Tech Stack
- Apache JMeter 5.6.3
- Restful Booker API
- CSV Data Set Config
- JSON Extractor (Correlation)
- JMeter HTML Report Dashboard

## Test Plans Included

| File | Purpose |
|---|---|
| booking-api-basic.jmx | Day 1 — First API test, JMeter fundamentals |
| booking-api-load-baseline.jmx | Day 2 — Load baseline with virtual users |
| booking-api-realistic-workload.jmx | Day 3 — Multi-API workflow with think time |
| booking-api-correlation-parameterization.jmx | Day 4 — Dynamic token + booking ID correlation |
| booking-api-assertions-reporting.jmx | Day 5 — Assertions + HTML report generation |
| booking-api-load-stress-test.jmx | Day 6 — Load and stress test 10→300 users |

## Booking Workflow Tested
Authenticate → Get Booking → Create Booking → Update Booking → Get Updated Booking


## Key Concepts Covered
- Thread Group — Virtual users, ramp-up, loop count
- Transaction Controller — End-to-end workflow measurement
- JSON Extractor — Auth token and Booking ID correlation
- CSV Data Set Config — Dynamic test data parameterization
- Think Time — Realistic user behaviour simulation
- Response Assertions — HTTP status code validation
- HTML Report Dashboard — Visual performance reporting

## Load Profile (Stress Test)

| Users | Avg RT (ms) | 95th % (ms) | Throughput | Error % |
|---|---|---|---|---|
| 10 | 637 | 2109 | 2.5/sec | 0.00% |
| 25 | 568 | 1883 | 5.6/sec | 0.00% |
| 50 | 746 | 2344 | 9.3/sec | 0.00% |
| 100 | 557 | 1875 | 14.4/sec | 0.00% |
| 150 | 535 | 1839 | 17.5/sec | 0.00% |
| 200 | 702 | 2279 | 19.1/sec | 1.93% |
| 300 | 634 | 2092 | 21.8/sec | 0.44% |

## How to Run

**Pre-requisite:** Apache JMeter 5.6.3 installed

**Run in GUI mode:**
Open JMeter → File → Open → select any .jmx file → Run


**Run in CLI mode (recommended for load tests):**
jmeter -n -t test-plans/booking-api-load-stress-test.jmx -l results/results.jtl -e -o results/html-report

**Generate HTML Report:**
jmeter -g results/results.jtl -o results/html-report

## Results
- Day 5 performance results and analysis: `docs/day-5-performance-results.md`
- Day 6 load/stress analysis: `docs/day-6-load-stress-results.md`
- JMeter HTML reports are generated automatically by GitHub Actions and available as workflow artifacts.