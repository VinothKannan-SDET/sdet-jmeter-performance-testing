# Performance Test Strategy

## Application
RESTful Booker API

## Objective
Evaluate API behavior under increasing concurrent user load.

## Tool
Apache JMeter

## Test Types
- Baseline testing
- Load testing
- Stress testing

## Workload
The test simulates users performing a realistic booking workflow:

1. Authenticate
2. Get Booking
3. Create Booking
4. Update Booking
5. Get Updated Booking

## Test Data
CSV Data Set Config provides dynamic booking data.

## Correlation
- Authentication token extracted from authentication response.
- Booking ID extracted from Create Booking response.

## Assertions
- HTTP response code validation
- Booking ID validation
- Updated booking data validation

## Metrics
- Average response time
- 90th/95th/99th percentile
- Throughput
- Error percentage

## Load Profile
10 → 25 → 50 → 100 → 150 → 200 → 300 users.

## Acceptance Criteria

| Metric 				| Threshold 		|
|-----------------------|-------------------|
| Average Response Time | < 1000 ms 		|
| 95th Percentile 		| < 3000 ms 		|
| Error Rate 			| < 1% 				|
| Throughput 			| > 10 requests/sec |

## Result Summary
Throughput increased as load increased. Errors appeared during the 200-user test, while the 300-user test showed a lower error rate. Results demonstrate load/stress behavior but do not establish production capacity.

## Limitations
The target is a public demo API. Therefore, results should be treated as learning/test-environment observations rather than production capacity measurements.