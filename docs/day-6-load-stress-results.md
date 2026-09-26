# Day 6 — Load & Stress Testing

## Objective
Evaluate application behavior as concurrent users increase.

## Test Results

| Users 	| Avg RT 	| 95% 	| 99% 	| Throughput 	| Error % |
|-----------|-----------|-------|-------|---------------|---------|
| 10 		| 637		| 2109	| 2439	| 2.5/sec		| 0.00%	  |
| 25 		| 568		| 1883	| 2203	| 5.6/sec		| 0.00%	  |
| 50 		| 746		| 2344	| 5244	| 9.3/sec		| 0.00%   |
| 100 		| 557		| 1875	| 2162	| 14.4/sec		| 0.00%   |
| 150 		| 535		| 1839	| 2087	| 17.5/sec		| 0.00%   |
| 200 		| 702		| 2279	| 4317	| 19.1/sec		| 1.93%   |
| 300 		| 634		| 2092	| 2409	| 21.8/sec		| 0.44%   |

## Acceptance Criteria Evaluation

| Metric 				| Threshold 	| Result at 150 users | Status  |
|-----------------------|---------------|---------------------|---------|
| Average Response Time | < 1000 ms 	| 535 ms 			  | ✅ PASS |
| 95th Percentile 		| < 3000 ms 	| 1839 ms 			  | ✅ PASS |
| Error Rate 			| < 1% 			| 0.00% 			  | ✅ PASS |
| Throughput 			| > 10 req/sec 	| 17.5/sec 			  | ✅ PASS |

**Conclusion:** The API meets all acceptance criteria up to
150 concurrent users. Criteria breached at 200 users
(Error Rate = 1.93% exceeds < 1% threshold).

## Observations

- Throughput increased from 2.5/sec to 21.8/sec.
- Error rate was 0% up to 150 users.
- 200 users produced 1.93% errors.
- 300 users produced 0.44% errors.
- No definitive breaking point was established.
- The 50-user 99th percentile showed a latency spike.

## Anomaly Observed

The 50-user test produced a 99th percentile of 5244ms
which is higher than the 100-user result of 2162ms.

Possible reasons:
- Short test duration amplifying outliers at 50-user level
- Network variance during that specific run
- API warm-up behaviour
- Public demo API instability

In a real project, this would trigger a re-run to confirm
whether the spike is consistent or a one-off observation.

## Key Learning

Load/stress testing should be evaluated using response time, percentiles, throughput and errors together.

The results represent observations from the test environment and should not be treated as production capacity.