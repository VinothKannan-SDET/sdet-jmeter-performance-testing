# JMeter Interview Notes

## 1. Why JMeter?
JMeter is used to simulate concurrent users and measure application performance.

## 2. What is a Thread Group?
It represents virtual users and controls users, ramp-up and iterations.

## 3. What is ramp-up?
The time JMeter takes to start the configured users.

## 4. What is correlation?
Capturing dynamic data from one response and using it in subsequent requests.

Example:
auth_token → Update Booking

booking_id → Get Updated Booking

## 5. What is parameterization?
Using external or dynamic test data instead of hardcoded values.

Example:
CSV Data Set Config.

## 6. What is throughput?
The number of requests processed per unit of time.

## 7. Why are percentiles important?
Average response time can hide slow requests. Percentiles show how the slower portion of requests behaved.

## 8. Load testing vs stress testing
Load testing evaluates expected workload.

Stress testing progressively increases load to observe degradation and failures.

## 9. Should Selenium generate performance load?
No. JMeter should generate the primary load. Selenium/Playwright can be used for limited UI validation while backend load is generated.

## 10. Can test results determine production capacity?
Not from this test alone. Capacity requires controlled infrastructure, realistic workload, longer tests and application/system monitoring.