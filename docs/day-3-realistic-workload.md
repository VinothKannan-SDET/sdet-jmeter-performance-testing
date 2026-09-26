# Day 3 — Realistic API Workload

## 1. What We Created

Created a realistic API workflow in JMeter using the Restful Booker API.

```text
Booking Workflow
│
├── 01 - Authenticate
├── Think Time - 2 sec
├── 02 - Get Booking
├── Think Time - 2 sec
└── 03 - Create Booking

## 2. Input / Configuration
| Setting                 | Value      |
| ----------------------- | ---------- |
| Virtual Users / Threads | 10         |
| Ramp-up                 | 10 seconds |
| Loop Count              | 5          |
| Think Time              | 2 seconds  |
| Requests per Workflow   | 3          |

APIs Used

POST /auth
GET  /booking
POST /booking

Create Booking Input
{
  "firstname": "Performance-1987",
  "lastname": "Test",
  "totalprice": 150,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2026-09-24",
    "checkout": "2026-09-30"
  },
  "additionalneeds": "Breakfast"
}

Headers:

Content-Type: application/json
Accept: application/json

## 3. Expected Execution

10 users × 5 loops = 50 workflows

50 workflows × 3 API requests
= 150 HTTP requests

## 4. Output / Results

Record the actual JMeter results below:

| Metric                | Result |
| --------------------- | -----: |
| Users                 |     10 |
| Workflow Executions   |     50 |
| Total HTTP Requests   |    150 |
| Average Response Time | 1392 ms (workflow) |
| Throughput            | 39.6/min           |
| Error %               | 0%                 |


API Results

| API              | Avg Response Time | Throughput | Error % |
| ---------------- | ----------------: | ---------: | ------: |
| Authenticate     | 398               | 48.1/min   | 0%      |
| Get Booking      | 660               | 48.4/min   | 0%      |
| Create Booking   | 333               | 48.2/min   | 0%      |
| Booking Workflow | 1392              | 39.6/min   | 0%      |
			
## 5. Issue Faced

Initially, Create Booking returned:

Response Code: 418
Response Message: I'm a teapot

Fix

Added the following header:

Accept: application/json

Final headers:

Content-Type: application/json
Accept: application/json

After this change, Create Booking worked successfully.

## 6. Key Learning
Created a multi-API performance workflow.
Used Transaction Controller to measure the complete workflow.
Used Think Time to simulate realistic user behaviour.
Understood that one workflow can contain multiple HTTP requests.
Understood basic API troubleshooting in JMeter.